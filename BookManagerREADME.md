**Book Collection Manager**

**Description**

This web application is designed to help you manage your book collection. It allows you to add, edit, and delete books, as well as search for books by title, author, or genre. The application is built using Flask, a Python web framework.

**Features**

* Add, edit, and delete books
* Search for books by title, author, or genre
* View a list of all books in your collection
* Export your book collection to a CSV file
* Import a book collection from a CSV file

**Getting Started**

1. Clone the repository: `git clone https://github.com/your-username/book-collection-manager.git`
2. Install the dependencies: `pip install -r requirements.txt`
3. Create a database: `flask db init`
4. Migrate the database: `flask db migrate`
5. Upgrade the database: `flask db upgrade`
6. Run the application: `flask run`

**Usage**

1. Visit the home page at http://localhost:5000/
2. Click on the "Add Book" link to add a new book to your collection.
3. Enter the title, author, genre, and publication date of the book.
4. Click on the "Create Book" button to save the book to your collection.
5. To edit a book, click on the "Edit" link next to the book's title.
6. Make the necessary changes to the book's information.
7. Click on the "Update Book" button to save the changes.
8. To delete a book, click on the "Delete" link next to the book's title.
9. Click on the "Confirm Delete" button to delete the book from your collection.
10. To search for a book, enter the search term in the search bar at the top of the page.
11. Click on the "Search" button to search for the book.
12. To export your book collection to a CSV file, click on the "Export" link at the top of the page.
13. To import a book collection from a CSV file, click on the "Import" link at the top of the page.

**Other Important Information**

* The application is configured to use SQLite as the database. You can change the database configuration in the `config.py` file.
* The application is deployed to Heroku at https://book-collection-manager.herokuapp.com/.
* The source code for the application is available on GitHub at https://github.com/your-username/book-collection-manager.