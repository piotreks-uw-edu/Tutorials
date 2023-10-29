# enter the scala intepreter
scala

# exit the Scala interpreter
Control-D

# defines a range of numbers from 1 through 10 (inclusive)
val nums = 1 to 10

# using the map function to transform each element of the nums sequence by doubling it
val doubledNums = nums.map( x => 2*x )

# using the reduce function to compute the sum of all elements in the doubledNums sequence
val sumOfDoubledNums = doubledNums.reduce( (x,y) => x+y )

# defining an immutable value that refers to a sequence of strings
val plays = Seq(
    "tamingoftheshrew", "comedyoferrors", "loveslabourslost", "midsummersnightsdream",
    "merrywivesofwindsor", "muchadoaboutnothing", "asyoulikeit", "twelfthnight")