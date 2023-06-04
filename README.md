# JS_Task_3
# JavaScript Simple Form Validation

This JavaScript file provides functionality to validate a simple form in a web page. It validates user input and displays error messages if the entered data does not meet the specified criteria.

## Usage

1. Include the JavaScript file in your HTML document using the `<script>` tag:

   ```html
   <script src="form-validation.js"></script>
   ```

2. Create an HTML form with input fields and a submit button:

   ```html
   <form id="myForm" onsubmit="validateForm(event)">
     <input type="text" id="name" placeholder="Name" required>
     <input type="email" id="email" placeholder="Email" required>
     <input type="password" id="password" placeholder="Password" required>
     <button type="submit">Submit</button>
   </form>
   ```

   Ensure that each input field has a unique `id` attribute and the form has an `id` attribute.

3. In your JavaScript code or within a `<script>` tag, define the `validateForm` function to perform form validation:

   ```javascript
   function validateForm(event) {
     event.preventDefault(); // Prevent form submission

     // Fetch form input values
     const nameInput = document.getElementById('name');
     const emailInput = document.getElementById('email');
     const passwordInput = document.getElementById('password');

     // Perform validation
     const name = nameInput.value.trim();
     const email = emailInput.value.trim();
     const password = passwordInput.value.trim();

     if (name === '') {
       showError(nameInput, 'Name is required');
       return;
     }

     if (email === '') {
       showError(emailInput, 'Email is required');
       return;
     }

     if (!isValidEmail(email)) {
       showError(emailInput, 'Invalid email format');
       return;
     }

     if (password === '') {
       showError(passwordInput, 'Password is required');
       return;
     }

     // Form is valid, perform further actions (e.g., submit form)
     // ...

     // Clear form input values
     nameInput.value = '';
     emailInput.value = '';
     passwordInput.value = '';
   }

   function showError(inputElement, message) {
     // Clear previous error message, if any
     const errorElement = inputElement.parentNode.querySelector('.error');
     if (errorElement) {
       errorElement.remove();
     }

     // Create and append new error message
     const error = document.createElement('div');
     error.className = 'error';
     error.textContent = message;
     inputElement.parentNode.appendChild(error);
   }

   function isValidEmail(email) {
     // Basic email validation
     const emailRegex = /\S+@\S+\.\S+/;
     return emailRegex.test(email);
   }
   ```

   Customize the validation logic and error messages according to your specific requirements.



When you submit the form without entering valid data, the validation logic will display error messages below the corresponding input fields. If the form is valid, the console will log "Form submitted" and the input fields will be cleared.

Feel free to customize the validation logic, error messages, and form submission behavior according to your specific requirements.
