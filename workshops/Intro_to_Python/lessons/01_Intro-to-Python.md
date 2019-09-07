# An Introduction to Python

Python is one of the most popular programming languages, and is widely used in a variety of fields. In particular, Python is used extensively for data science owing to the large number of open-source machine learning and data science libraries written for Python. Python code is designed to be easy to write and easy to read, keeping unnecessary details (such as memory management) hidden from the programmer and user.

While Python often gets a lot of flack for being slower than other languages such as C++ or Fortran, modern Python libraries such as Numpy and TensorFlow are highly optimized for numerical computation, largely eliminating this speed difference.

In this tutorial we will cover some of the basics of Python, with a focus on usage in a scientific computing setting.

This is not intended to be a comprehensive tutorial, but rather a taste of what is possible with Python, as well as providing a general foundation for you to go and explore Python further.


## Part 1: Features of Python


> Python is an interpreted, high-level, general-purpose programming language. *--Wikipedia*

- No need to compile code before running it (interpreted vs compiled)
- Low-level details such as memory-management are hidden from the user (high-level)
- Can be used for a wide variety of tasks, including web-programming, scientific analysis, server management, file manipulation etc. (general purpose).

## A brief note about Python versions...

Python 2.7 was the most commonly used Python version for a long time, but it has now reached the end of it's life. A number of breaking changes were introduced in Python 3, making conversion between Python 2 and 3 difficult.

Most major scientific computing projects (Numpy, Scipy etc) are ceasing support for Python 2.7 from 2020 onwards. Under no circumstances should you be writing new code in Python 2.7!!

For any new projects, use Python 3 (ideally one of the more recent version - >3.7).


[**Next Lesson: Variables and data types**](https://andrewguy.github.io/Training/workshops/Intro_to_Python/lessons/02_variables-and-data-types)