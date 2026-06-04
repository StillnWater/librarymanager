# Library Manager

A Python-based library management system for managing book inventory, tracking book status, and handling book checkout/return operations.

## Features

- **Add Books**: Add new books to the library inventory with title, author, and ISBN
- **Issue Books**: Check out books from the library (mark as issued)
- **Return Books**: Return issued books to the library (mark as available)
- **Search Functionality**: Search books by title or ISBN
- **View Inventory**: Display all books in the library with their current status
- **Data Persistence**: Automatically save and load inventory from a JSON file
- **Logging**: Track all operations with a comprehensive logging system
- **Error Handling**: Robust exception handling for user inputs and file operations

## Project Structure

```
librarymanager/
├── main.py          # Interactive CLI menu and main application
├── book.py          # Book class definition
├── inventory.py     # LibraryInventory class for managing the book collection
└── library.json     # Persistent storage for book data (auto-generated)
```

## Usage

### Running the Application

```bash
python main.py
```

### Menu Options

```
--- Library Management System ---
1. Add Book              - Add a new book to inventory
2. Issue Book           - Check out a book (mark as issued)
3. Return Book          - Return an issued book
4. Search by Title      - Find books by title (case-insensitive)
5. View All Books       - Display all books in inventory
6. Exit                 - Exit the application
```

### Example Workflow

1. **Add a Book**:
   - Select option `1`
   - Enter title, author, and ISBN
   - Book will be added to inventory with "available" status

2. **Issue a Book**:
   - Select option `2`
   - Enter the ISBN of the book
   - Book status changes to "issued"

3. **Return a Book**:
   - Select option `3`
   - Enter the ISBN of the book
   - Book status changes to "available"

4. **Search for Books**:
   - Select option `4`
   - Enter a search term (partial matches work)
   - All matching books will be displayed

## Implementation Details

### Book Class (`book.py`)
- Represents a single book with properties: title, author, ISBN, and status
- Methods:
  - `issue()`: Mark book as issued (if available)
  - `return_book()`: Mark book as available
  - `is_available()`: Check availability status
  - `to_dict()`: Convert book object to dictionary for JSON serialization

### LibraryInventory Class (`inventory.py`)
- Manages the collection of books
- Features:
  - **Duplicate Detection**: Prevents adding books with duplicate ISBNs
  - **Search**: Find books by title (case-insensitive) or ISBN
  - **Data Persistence**: Saves/loads inventory from `library.json`
  - **Logging**: Records all operations to `library.log`
  - **Error Handling**: Graceful handling of corrupted database files

### Main Application (`main.py`)
- Interactive CLI with menu-driven interface
- Input validation for required fields
- Exception handling for unexpected errors
- Persistent state management

## Data Storage

The application uses a JSON file (`library.json`) to store book data:

```json
[
  {
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "isbn": "978-0743273565",
    "status": "available"
  },
  {
    "title": "To Kill a Mockingbird",
    "author": "Harper Lee",
    "isbn": "978-0061120084",
    "status": "issued"
  }
]
```

## Logging

All operations are logged to `library.log` with timestamps and log levels (INFO, WARNING, ERROR). This includes:
- Books added/removed
- Duplicate ISBN attempts
- Database load/save operations
- Errors and exceptions

## Requirements

- Python 3.x
- No external dependencies (uses only Python standard library)

## Error Handling

The application includes comprehensive error handling for:
- Missing required input fields
- Non-existent books (ISBN not found)
- Already issued books
- Corrupted JSON database files
- File I/O errors
- Unexpected runtime errors

## Author

Manas Bhasker

## License

No specific license specified. See repository for details.
