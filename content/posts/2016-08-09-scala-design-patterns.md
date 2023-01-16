---
title: "Scala Design Patterns Summary"
summary: "Here is a set of common scala design patterns which I used in my coding time."
date: "2022-12-01"
categories: Tech
tags: ["Scala"]
---

Here is a set of common scala design patterns which I used in my coding time.

## 1. Factory
```scala
trait Vehicle {
  def drive
}

class Car extends Vehicle {
  override def drive {
    printf("car bibi~")
  }
}

class Bus extends Vehicle {
  override def drive {
    printf("bus didi~")
  }
}

class Truck extends Vehicle {
  override def drive {
    printf("truck wowo~")
  }
}

object Vehicle {
  def apply(kind: String) = kind match {
    case "car" = new Car()
    case "bus" = new Bus()
    case "truck" = new Truck()
  }
}
```

## 2. Adapter
```scala
import java.util.logging.Level
import java.util.logging.Level._

object Adapter extends App {
  trait Log {
    def warn(msg: String)
    def error(msg: String)
  }

  final class Logger {
    def log(level: Level, message: String) = {}
  }

  implicit class LoggerToLogAdapter(logger: Logger) extends Log {
    def warn(msg: String) = { logger.log(WARNING, msg) }
    def error(msg: String) = { logger.log(INFO, msg) }
  }

  val log = new Logger()

  log.warn("warn")
  log.error("error")
}
```

## 3. Decorator
```scala
// 在以下两种情况下可以考虑使用装饰器模式：
// (1)需要在不影响其他对象的情况下，以动态、透明的方式给对象添加职责。
// (2)如果不适合使用子类来进行扩展的时候，可以考虑使用装饰器模式。


object Decorator extends App {
  trait OutStream {
    def write(b: Array[Byte])
  }

  class FileOutputStream(path: String) extends OutStream {
    override def write(b: Array[Byte]) = {
      println("do something")
    }
  }

  trait Buffering extends OutStream {
    abstract override def write(b: Array[Byte]) = {
      println("do something before super.write buffering")
      super.write(b)
    }
  }

  new FileOutputStream("hi") .write("hi fileoutput stream".getBytes())

  (new FileOutputStream("hi") with Buffering).write("buffering".getBytes())
}
```

## 4. Strategy
```scala
object Strategy extends App {
  type Strategy = (Int, Int) => Int
  class Context(s: Strategy) {
    def use(a: Int, b: Int) = s(a, b)
  }

  val add: Strategy = _ + _

  println(new Context(add).use(2, 3))
}
```

## 5. Chain of Responsibility
```scala
object Chain extends App {

  case class Event(source: String)
  trait Handler {
    def handle(event: Event)
  }

  class DefaultHandler extends Handler {
    def handle(event: Event) = { println("default handler handle")}
  }

  trait KeyboardHandler extends Handler {
    abstract override def handle(event: Event): Unit = {
      if (event.source == "keyboard") {
        println("keyboard handler handle")
      } else {
        super.handle(event)
      }
    }
  }

  trait MouseHandler extends Handler {
    abstract override def handle(event: Event): Unit = {
      if (event.source == "mouse") {
        println("mouse handler handle")
      } else {
        super.handle(event)
      }
    }
  }

  val handler = new DefaultHandler with KeyboardHandler with MouseHandler

  handler.handle(new Event(source  = "a"))
  handler.handle(new Event(source  = "keyboard"))
  handler.handle(new Event(source  = "mouse"))

}
```

## 6. Dependency Injection
```scala
object CI extends App {

  case class User()

  trait Repository {
    def save(user: User)
  }

  trait DefaultRepository extends Repository {
    def save(user: User) = {
      println("save user")
    }
  }

  trait UserService { self: Repository =>
    def create(user: User): Unit = {
      save(user)
    }
  }

  (new UserService with DefaultRepository).create(new User)

}
```