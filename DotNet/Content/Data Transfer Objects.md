
## What are DTOs?

> The content below (definition of DTOs) is from the official [ASP.NET documentation](https://learn.microsoft.com/en-us/aspnet/web-api/overview/data/using-web-api-with-entity-framework/part-5).

The client receives data that maps directly to your database tables. However, that's not always a good idea. Sometimes you want to change the shape of the data that you send to client. For example, you might want to:

- Remove circular references.
- Hide particular properties that clients are not supposed to view.
- Omit some properties in order to reduce payload size.
- Flatten object graphs that contain nested objects, to make them more convenient for clients.
- Avoid "over-posting" vulnerabilities. 
- Decouple your service layer from your database layer.

To accomplish this, you can define a _data transfer object_ (DTO). A DTO is an object that defines how the data will be sent over the network.
### Creating a details DTO for our Book Entity

-  Considering that we want the API users to only be able to see the *Title, Sinopsis and Author* when they check for an specific book, the DTO will be like this:

```
public class BookDetailsDTO
{
    public string Title { get; set; }
    public string Sinopsis { get; set; }
    public Author Author { get; set; }
}
```
