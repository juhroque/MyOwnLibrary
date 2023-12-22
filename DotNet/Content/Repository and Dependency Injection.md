## Repository Pattern 

-  It is a  software design pattern that acts as an intermediary between the business logic and the data storage.
-  It provides a consistent interface for performing CRUD (Create, Read, Update, Delete) operations on data entities while encapsulating the complexities of data access. 

#### Create the repositories

**Important**: create all of them in a specific folder. Also create a specific folder for the *interfaces*.

1. Create the Repository Interface for each Entity.
2. Implement the interface in the Repository class for each one, creating the logic for the methods.

**Books**

*Interface*:
```
    public interface IBookRepository
    {
        ICollection<Book> GetBooks();
    }
}
```

*Class*:

```
public class BookRepository : IBookRepository
{
    private readonly DataContext _context;

    public BookRepository(DataContext context)
    {
        _context = context;
    }

    public ICollection<Book> GetBooks()
    {
        return _context.Books.OrderBy(b => b.Id).ToList();
    }
}
```


-  Notice that we use *Dependency Injection* in the repository constructor. (Explained more deeply in the [Controllers](DotNet/Content/Controllers.md) section.)

Add this line to the ***Program.cs*** file:

`builder.Services.AddScoped<IBookRepository, BookRepository>();`

