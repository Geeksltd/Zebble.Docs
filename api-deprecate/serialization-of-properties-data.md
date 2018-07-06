
### SERIALIZATION OF PROPERTIES' DATA

To prevent accidental exposure of data, you are required to explicitly mark the properties of the server type that you want available to the API.

To achieve this you should add **[JsonExposed]** attribute on top of those properties.
In M# you can just set it on each property with a boolean flag which will then add the attribute for you automatically.

**NOTE:**

If you want the property name to be different for the API then you can use **[JsonProperty(PropertyName="AnotherName")]**.