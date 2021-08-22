## Circuit Breaker Pattern


Overview

![A Soviet/Russian 100kV three single phase oil Circuit Breaker. (*Do not judge the size of a Circuit breaker by its cover photo*)](https://cdn.hashnode.com/res/hashnode/image/upload/v1629634073035/yYZuKjJxq.jpeg)*A Soviet/Russian 100kV three single phase oil Circuit Breaker. (*Do not judge the size of a Circuit breaker by its cover photo*)*

According to Wikipedia the definition of Circuit Breaker in Electrical technology.

*A [circuit breaker](https://en.wikipedia.org/wiki/Circuit_breaker) is an automatically operated [electrical](https://en.wikipedia.org/wiki/Electricity) [switch](https://en.wikipedia.org/wiki/Switch) designed to protect an [electrical circuit](https://en.wikipedia.org/wiki/Electrical_network) from damage caused by excess current from an overload or [short circuit](https://en.wikipedia.org/wiki/Short_circuit). Its basic function is to interrupt current flow after a fault is detected. Unlike a [fuse](https://en.wikipedia.org/wiki/Fuse_(electrical)), which operates once and then must be replaced, a circuit breaker can be reset (either manually or automatically) to resume normal operation.*

And in Software designing:

*A [Circuit breaker](https://en.wikipedia.org/wiki/Circuit_breaker_design_pattern) is a [design pattern](https://en.wikipedia.org/wiki/Design_pattern_(computer_science)) used in modern [software development](https://en.wikipedia.org/wiki/Software_development). It is used to detect failures and encapsulates the logic of preventing a failure from constantly recurring, during maintenance, temporary external system failure or unexpected system difficulties.*

Though the name of this pattern borrowed from Electrical Engineering, in the Software world the Circuit breaker (CB) design pattern can do much more than just tripping a circuit with failures like:

* In between fully opened and fully closed state, CB can have an intermediate state, called Half-open state where an application can operate at degraded functionalities

* Automatic checking of the state of the application is possible.

* Once the application status turns green, then auto normalization of application functionalities,

This pattern describes how to safely connect different parts of the system to avoid the cascading failures across the system. In Electrical engineering, in order to protect electrical circuits from each other and introduce decoupled failure domains, a technique was established to breaking the connection when the transmitted power exceeds a certain threshold i.e. Circuit Breaker.

## Background

In distributed architecture filled with Microservices remote calls between service to service is a frequent phenomenon. One of the challenges of any distributed architecture is managing remote process service responsiveness. Usually, a Time-out value is kept before the service consumer throws back the unresponsiveness of the service.

For e.g., suppose you are making a service request to buy 100 shares of *Microsoft *and unfortunately the service consumer is time out the request right when the service has successfully placed the trade and is about to give you a confirmation number. You can try to resubmit the trade, but you have to add significant complexity into your service to determine if this is a new trade or a duplicate trade. Furthermore, since you don’t have a confirmation number from the first trade it is very difficult to know whether the trade was actually successful or not.

Usually, a timeout value is peak load performance time multiplied by 2 i.e. if a service gives a response in 2 seconds and 3 seconds in normal and peak load respectively, then the time out value should be 6 seconds. Initially, this idea seems good. However, later on, when we create a waiting time period of 6 seconds for each request call to determine whether the service is available does not sound like a good idea. Usually, the end-users click submits button within 2–3 seconds of no response. To solve this anti-pattern Circuit breaker design pattern can be used, which can improve the stability and resiliency of an application.

The basic idea behind the circuit breaker is very simple. You wrap a protected function call in a circuit breaker object, which monitors for failures. Once the failures reach a certain threshold, the circuit breaker trips, and all further calls to the circuit breaker return with an error, without the protected call being made at all. Usually, you’ll also want some kind of monitor alert if the circuit breaker trips.

## Circuit Breaker stages

A Circuit Breaker component has the following three stages:

* Closed

* Open

* Half-Open

![Three stages of a Circuit Breaker](https://cdn.hashnode.com/res/hashnode/image/upload/v1629634074749/Zaqv7VkOB.png)*Three stages of a Circuit Breaker*

The Predefined number of times is the number of exceptions threshold need to be configured along with the Timeout value for each CB.

## CLOSED state

Initially, the Circuit Breaker enters into a CLOSED state and waits for Client Requests. In the CLOSED state, it does the following things:

1. It receives Client Requests and makes a call to the Service

1. If it succeeds and receives the response from that Service, it will reset the failure count to 0 and send that response back to the end user.

1. If it fails to receive the response from that Service, it will increment the failure count by one and check whether that count is greater than the predefined failure threshold

1. If the failure count is greater than the failure threshold, then that Circuit Breaker component trips or enters into the OPEN state

## OPEN state

In the OPEN state, it does the following things:

1. The Circuit Breaker component enters into this state when the failure count is greater than the failure threshold

1. When it is in this state, it does not make a call to the Service

1. When it is in this state, if the Client sends any requests to it, it won’t make a call to the Service; it just sends an Exception and waits for some time i.e. the Timeout value specified

1. Once the Timeout value expires, it will enter into the HALF-OPEN state

## HALF-OPEN state

In the HALF-OPEN state, it does the following things:

1. The Circuit Breaker component enters into this state when it finishes the predefined waiting time.

1. It sends the first request to the Service.

1. If it receives a success response, then it will enter into the CLOSED state to process further Client Requests. Before picking up the first client request, it will reset the failure count to 0 again.

1. If it receives a failure response, then it will re-trip to the OPEN state and wait for a predefined Timeout value to expire.

## When to use this Pattern

Use this pattern:

* To prevent an application from attempting to invoke a remote service or access a shared resource if this operation is highly likely to fail.

This pattern might not be suitable:

* For handling access to local private resources in an application, such as in-memory data structure. In this environment, using a circuit breaker would simply add overhead to your system.

* As a substitute for handling exceptions in the business logic of your applications.

For Issues and Considerations, more use cases and examples please visit the [MSDN Blog](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/dn589784(v=pandp.10))

[Hystrix library](https://github.com/Netflix/Hystrix/wiki/How-it-Works#circuit-breaker) of Netflix has sequence diagrams on how Netflix implemented the Circuit Breaker pattern in their services.

## Implementation of Circuit Breaker pattern

## In Python

[pybreaker](https://github.com/danielfm/pybreaker) library can be used to implement this pattern.

```
import pybreaker
import redis

redis = redis.StrictRedis()  # redis client instantiat
db_breaker = pybreaker.CircuitBreaker(
    fail_max=5, # maximum continuous exceptions threshold limit
    reset_timeout=60, # rechecking the redis DB status
    state_storage=pybreaker.CircuitRedisStorage(pybreaker.STATE_CLOSED, redis))
```


The DB is initialized above with *db_breaker* object as circuit breaker instance.

```
@db_breaker
def update_customer(cust):*# Do stuff here...pass*

*# Will trigger the circuit breaker*
updated_customer = update_customer(my_customer)
```


According to the default parameters, the circuit breaker db_breaker will automatically open the circuit after 5 consecutive failures in update_customer.

When the circuit is open, all calls to *update_customer* will fail immediately (raising *CircuitBreakerError*) without any attempt to execute the real operation.

After 60 seconds, the circuit breaker will allow the next call to *update_customer* pass through. If that call succeeds, the circuit is closed; if it fails, however, the circuit is opened again until another timeout i.e. 60 seconds elapses. The cycle continues till the call succeeds without exception.

By default, a failed call is any call that raises an exception. However, it's common to raise exceptions to also indicate business exceptions, and those exceptions should be ignored by the circuit breaker as they don't indicate system errors. These excluding exceptions are supported in *pybreaker*. Monitoring and management details are supported too.

## Implementation in other languages

* [Jrugged](https://github.com/Comcast/jrugged) library for implementation in Java

* Akka Toolkit’s [CircuitBreaker Component ](https://github.com/akka/akka/blob/master/akka-actor/src/main/scala/akka/pattern/CircuitBreaker.scala)implementation in Scala

* [MSDN blog](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/dn589784(v=pandp.10)) for implementation in C#

* [Martin Fowler’s blog](https://martinfowler.com/bliki/CircuitBreaker.html) for implementation in Ruby.

Thanks for your time. Please suggest any improvements if needed..

## References

* [Microservices Anti-patterns and Pitfalls](https://www.oreilly.com/ideas/microservices-antipatterns-and-pitfalls) by Mark Richard

* [Scala reactive programming](https://www.amazon.com/Scala-Reactive-Programming-functional-microservices/dp/1787288641) by Rambabu Posa

* [CircuitBreaker](https://martinfowler.com/bliki/CircuitBreaker.html) by Martin Fowler

* [Circuit Breaker Pattern](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/dn589784(v=pandp.10)) by Microsoft Developer Network

* [Pybreaker](https://github.com/danielfm/pybreaker) from Daniel Martins et al