# fireworks-in-scala
import scala.util.Random

case class Firework(x: Double, y: Double, color: Int)

val r = new Random()

def createFirework(x: Double, y: Double): Firework = {
  val color = r.nextInt(5)
  Firework(x, y, color)
}

def draw(fw: Firework) {
  val symbol = fw.color match {
    case 0 => "*"
    case 1 => "o"
    case 2 => "x"
    case 3 => "^"
    case 4 => ">"
  }
  println(s"${fw.x}, ${fw.y}: $symbol")
}

val fireworks = for {
  x <- 0 to 10
  y <- 0 to 10
} yield createFirework(x, y)

fireworks.foreach(draw)
