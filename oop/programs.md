# Programs are Classes and Vice Versa

It may surprise you to know
that you have already seen several class definitions
in this tutorial.
If you have written a program in Pike,
you have also written a class.
This is because in Pike,
programs and classes are the same,
and the terms **program** and **class**
are sometimes used as synonyms.

A Pike program in a file is a class definition.
The methods that you have defined in the file
are the methods of the class,
and the global variables
(that is, the variables defined outside the methods)
are the member variables.
If you like,
you can imagine that
the file has an implicit "`class { }`" around the code.
But it would be bothersome
if we had to put every little class in its own file,
so we also have the "`class { }` notation.

To create the equivalent of the class `animal`,
which we defined above,
we would need a file with the following contents.
The file name can be "animal.pike",
but any name will work.

```pike
string name;

float weight;

void create(string n, float w)
{
  name = n;
  weight = w;
}

void eat(string food)
{
  write(name + " eats some " + food + ".\n");
  weight += 0.5;
}
```

We can't use a string as a type name,
so the file name won't work as a data type:

```pike
"animal.pike" my_dog; // Doesn't work at all.
```

Instead,
we must let Pike read and compile the file,
making a **program** of it
(or **class**, if you prefer that term,
but the data type is `program`),
and then we put that program in a **constant**:

```pike
constant animal = (program)"animal.pike";
```

Now you can use `animal` as the class name,
just as before:

```pike
animal piglet = animal("Piglet", 6.3);
```
