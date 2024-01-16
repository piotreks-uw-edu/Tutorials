### case class definition
case class Student(
firstName: String,
lastName: String,
favoriteColor: String,
favoriteNumber: Int,
favoriteFood: String
)

### Creating an Instance of a Case Class
val student = Student(
firstName = "John",
lastName = "Stockton",
favoriteColor = "Brown",
favoriteNumber = 7,
favoriteFood = "Steak"

### Creating a modified instance of a Case Class
val newStudent = student.copy(
favoriteColor = "Orange",
favoriteFood = "Potatoes"
)

### Pattern Matching and Case Classes
case class Person(firstName: String, lastName: String)
object Yoda {
def respondTo(person: Person): String = person match {
case Person("Luke", "Skywalker") => "I cannot teach him. The boy has no
patience."
case Person("Leia", "Organa") => "There is another."
case Person("Chewbacca", _) => "Good relations with the Wookiees I have."
case Person("Darth", "Vader") => "Worked out well, that did, yes? No."
case _ => "This person is unknown to me."
}
}
val response1 = Yoda.respondTo(Person("Luke", "Skywalker"))
val response2 = Yoda.respondTo(Person("Leia", "Organa"))
val response3 = Yoda.respondTo(Person("Mr.", "Spock"))