# Mobile Contacts - SOA Introductory Project

## Overview
This project is a **Service-Oriented Architecture (SOA)** introductory application designed to manage mobile contacts. It follows a layered architecture with controllers, data access objects (DAO), data transfer objects (DTO), and exception handling.

## Features
- Interactive **menu-based CLI** for managing contacts
- Add new mobile contacts
- Retrieve mobile contacts
- Update existing contacts
- Delete contacts
- Search contacts
- Handle errors with custom exceptions
- Uses **DTO (Data Transfer Objects)** to encapsulate request and response data

## Project Structure
```
/mobilecontacts
├── Main.java                           # Entry point of the application, includes CLI menu
├── controller/
│   ├── MobileContactController.java    # Handles API requests for contacts
├── core/serializer/
│   ├── Serializer.java                 # Handles object serialization
├── dao/
│   ├── IMobileContactDAO.java          # Interface for data access operations
│   ├── MobileContactDAOImpl.java       # Implementation of data access operations
├── dto/
│   ├── BaseDTO.java                     # Base Data Transfer Object
│   ├── MobileContactInsertDTO.java      # DTO for inserting contacts
│   ├── MobileContactReadOnlyDTO.java    # DTO for reading contacts
│   ├── MobileContactUpdateDTO.java      # DTO for updating contacts
├── exceptions/
│   ├── ContactNotFoundException.java    # Custom exception for not found contacts
```

## Setup Instructions

### Prerequisites
Ensure you have **Java 11+** installed.

### Build & Run
1. **Clone the repository** (or place files in a working directory)
2. **Compile the project:**
   ```sh
   javac -d bin $(find . -name "*.java")
   ```
3. **Run the application:**
   ```sh
   java -cp bin Main
   ```

## Usage

### Interactive CLI Menu
When you run the application, you will be presented with a **menu** where you can perform the following operations:
```
1. Add Contact
2. Update Contact
3. Delete Contact
4. Search Contact
5. Show All Contacts
6. Exit
```
Simply enter the corresponding number to perform an action.

### Add a Mobile Contact
To insert a new contact, use the `MobileContactInsertDTO`:
```java
MobileContactInsertDTO contact = new MobileContactInsertDTO("John Doe", "1234567890");
mobileContactController.addContact(contact);
```

### Retrieve a Contact
Use `MobileContactReadOnlyDTO` to fetch contact details:
```java
MobileContactReadOnlyDTO contact = mobileContactController.getContactById(1);
System.out.println(contact.getName());
```

### Update a Contact
To update an existing contact:
```java
MobileContactUpdateDTO updatedContact = new MobileContactUpdateDTO(1, "John Smith", "0987654321");
mobileContactController.updateContact(updatedContact);
```

### Delete a Contact
To delete a contact:
```java
mobileContactController.deleteContact(1);
```

### Error Handling
If a contact is not found, a `ContactNotFoundException` is thrown:
```java
try {
    MobileContactReadOnlyDTO contact = mobileContactController.getContactById(99);
} catch (ContactNotFoundException e) {
    System.out.println("Contact not found!");
}
```

## Contribution
Feel free to fork this repository, create a feature branch, and submit a pull request with improvements!

## License
This project is licensed under the **MIT License**.

