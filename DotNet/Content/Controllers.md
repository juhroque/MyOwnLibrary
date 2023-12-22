**Important**: to understand the informations provided below, it is mandatory to know basic *HTTP* and [Data Transfer Objects](Content/Data%20Transfer%20Objects.md) concepts.
## Understanding and creating the controller

-  A controller is a class that processes incoming HTTP requests, performs the necessary actions, and produces an HTTP response.

- By ***injecting*** the repository interface into your business logic classes, you decouple them from the specific repository implementation, making it easier to switch repositories or mock them during testing.

```
public class BookController : Controller
{
    private readonly IBookRepository _bookRepository;

    public BookController(IBookRepository bookRepository)
    {
        _bookRepository = bookRepository;
    }
}
```
## Get methods

```
[HttpGet]
[ProducesResponseType(200, Type = typeof(IEnumerable<Book>))]
public IActionResult GetAllBooks()
{
    var books = _bookRepository.GetBooks();
    if(!ModelState.IsValid)
	    return BadRequest(ModelState);
    return Ok(books);
}

```
