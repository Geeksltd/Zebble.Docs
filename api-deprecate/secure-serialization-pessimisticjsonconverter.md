
### SECURE SERIALIZATION: PESSIMISTICJSONCONVERTER

By default, Json.NET will serialize all properties unless you have [JsonIgnore] added. That is insecure and can lead to accidental exposure of sensitive data.

To solve that in M# you should set **"Secure Json Serializations"** to **true** at the project level. It will then add an attribute on all classes to tell Json.NET to use the **PessimisticJsonConverter** instead, which works in the opposite way to its default converter: I.e. it will ignore all properties unless they explicitly have the [**JsonExposed**] attribute.