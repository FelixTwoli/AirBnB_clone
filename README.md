# AirBnB_clone
Background Context
The goal of the project is to deploy on your server a simple copy of the AirBnB website. At the end, we will have a complete web application composed of:

A command interpreter to manipulate data without a visual interface, like in a Shell (perfect for development and debugging)
A website (the front-end) that shows the final product to everybody: static and dynamic
A database or files that store data (data = objects)
An API that provides a communication interface between the front-end and your data (retrieve, create, delete, update them)
(The Holberton B&B)
In this project, we will clone Airbnb by doing the following:
put in place a parent class (called BaseModel) to take care of the initialization, serialization and
create a simple flow of serialization/deserialization: Instance <-> Dictionary <-> JSON string <-> file
create all classes used for AirBnB (User, State, City, Place ...) that inherit from BaseModel
create the first abstracted storage engine of the project: File storage.
create all unittests to validate all our classes and storage engine
Files
models/base_model.py
Defines all common attributes/methods for other classes:
Public instance attributes:

id - string - assigned with an uuid when an instance is created
created_at - datetime - assigned with the current datetime when an instance is created
updated_at - datetime - assign with the current datetime when an instance is created and it will be updated every time you change your object
Public instance methods:

save(self) - updates the public instance attribute updated_at with the current datetime

to_dict(self) - returns a dictionary containing all keys/values of dict of the instance.

__str__ - prints [<class name>] (<self.id>) <self.__dict__>

models/init.py
Creates a unique FileStorage instance called storage for the application that is used to reload previous objects created.

models/engine/file_storage.py
This class has methods that serializes a python dictionary to JSON string and reverses the process from JSON string to a python dictionary

Private class attributes:

__file_path - string - path to the JSON file
__objects - dictionary - empty but will store all objects by .id
Public instance methods:
all(self) - returns the dictionary __objects
new(self, obj) - sets in __objects the obj with key .id
save(self) - serializes __objects to the JSON file (path: __file_path)
reload(self) - deserializes the JSON file to __objects (only if the JSON file (__file_path) exists
Installation
git clone git@github.com:Janengethe/AirBnB_clone.git
cd AirBnB_clone
Usage
Interactive Mode

$ ./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  help  quit

(hbnb)
(hbnb)
(hbnb) quit
$
Non-Interactive Mode

$ echo "help" | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb)
$
$ cat test_help
help
$
$ cat test_help | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb)
$
Author
Felix Twoli
