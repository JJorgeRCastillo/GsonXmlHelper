# GsonXmlHelper
GsonXmlHelper is a little library to work with API's and WebServices that return XML structure and you can consume it into your application. 
This library is build with Java 1.8 JDK

# Content
This little library have two classes that will help the use of XML parsing without declaring SerializedName in your attributes, it just directly maps to your class all the values, you just take care that you have to send from your database query the same name of your class attributes.
* The first class is: 
ListGeneric, this class allows you to create a generic type of objectos from your domain.
* The second class is: 
GsonXmlHelper, this class makes all the work behind the scenes to map your XML nodes to your object dynamically.

#Example
If you are consuming a list of objects or just one object you just have to use this structure.
We will use an example to get all the courses from a school.
```java
//1.- Declare a List of Course Objects
List<Course> listCourses;

//2.- Call GsonXmlHelper.getGsonToXml() method that creates a GsonXml object with the configuration
GsonXml gxml = GsonXmlHelper.getGsonToXml();

//3.- Get data from the call, the 'content' parameter is our xml response from the server.
//To get the content, you have to implement a class that get the content from the endpoint url
//to test this library, just send an xml with the structure of your class and this method will map each node.
listCourses = gxml.<ListGeneric>fromXml(content, new TypeToken<ListGeneric<Course>>(){}.getType()).getList();
```
