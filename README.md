**# BudgetAPp**
we will learn how to create a budget app. To build this app, we need HTML, CSS and Javascript.

Let us take a look at how this app works. Our budget app has two input sections. We use the first input section to set/update the budget. And we use the other input to enter the expense title and expense amount.

As soon as the user sets the budget or adds an expense, we display an output that shows the budget, total expenses, and the balance left.

Following this output, we display a list of all the expenses. This list of items comes with an option to either edit or delete them.
Project Folder Structure:
Before we start coding let us take a look at the project folder structure. We create a project folder called – ‘ Budget App’. Inside this folder, we have three files. These files are index.html which is an HTML document. Next, we have style.css which is the stylesheet. Finally, we have script.js which is a script file.

HTML: 
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Budget App</title>
    <!-- Font Awesome Icons -->
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css"
    />
    <!-- Google Fonts -->
    <link
      href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500&display=swap"
      rel="stylesheet"
    />
    <!-- Stylesheet -->
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="wrapper">
      <div class="container">
        <div class="sub-container">
          <!-- Budget -->
          <div class="total-amount-container">
            <h3>Budget</h3>
            <p class="hide error" id="budget-error">
              Value cannot be empty or negative
            </p>
            <input
              type="number"
              id="total-amount"
              placeholder="Enter Total Amount"
            />
            <button class="submit" id="total-amount-button">Set Budget</button>
          </div>

          <!-- Expenditure -->
          <div class="user-amount-container">
            <h3>Expenses</h3>
            <p class="hide error" id="product-title-error">
              Values cannot be empty
            </p>
            <input
              type="text"
              class="product-title"
              id="product-title"
              placeholder="Enter Title of Product"
            />
            <input
              type="number"
              id="user-amount"
              placeholder="Enter Cost of Product"
            />
            <button class="submit" id="check-amount">Check Amount</button>
          </div>
        </div>
        <!-- Output -->
        <div class="output-container flex-space">
          <div>
            <p>Total Budget</p>
            <span id="amount">0</span>
          </div>
          <div>
            <p>Expenses</p>
            <span id="expenditure-value">0</span>
          </div>
          <div>
            <p>Balance</p>
            <span id="balance-amount">0</span>
          </div>
        </div>
      </div>
      <!-- List -->
      <div class="list">
        <h3>Expense List</h3>
        <div class="list-container" id="list"></div>
      </div>
    </div>
    <!-- Script -->
    <script src="script.js"></script>
  </body>
</html>
CSS:
Next, we style the app with CSS. For this copy, the code provided to you below and paste it into your stylesheet.
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}
body {
  background-color: #f7f9fd;
}
.wrapper {
  width: 90%;
  font-size: 16px;
  max-width: 43.75em;
  margin: 1em auto;
}
.container {
  width: 100%;
}
.sub-container {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3em;
}
.flex {
  display: flex;
  align-items: center;
}
.flex-space {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.wrapper h3 {
  color: #363d55;
  font-weight: 500;
  margin-bottom: 0.6em;
}
.container input {
  display: block;
  width: 100%;
  padding: 0.6em 0.3em;
  border: 1px solid #d0d0d0;
  border-radius: 0.3em;
  color: #414a67;
  outline: none;
  font-weight: 400;
  margin-bottom: 0.6em;
}
.container input:focus {
  border-color: #587ef4;
}
.total-amount-container,
.user-amount-container {
  background-color: #ffffff;
  padding: 1.25em 0.9em;
  border-radius: 0.3em;
  box-shadow: 0 0.6em 1.2em rgba(28, 0, 80, 0.06);
}
.output-container {
  background-color: #587ef4;
  color: #ffffff;
  border-radius: 0.3em;
  box-shadow: 0 0.6em 1.2em rgba(28, 0, 80, 0.06);
  margin: 2em 0;
  padding: 1.2em;
}
.output-container p {
  font-weight: 500;
  margin-bottom: 0.6em;
}
.output-container span {
  display: block;
  text-align: center;
  font-weight: 400;
  color: #e5e5e5;
}
.submit {
  font-size: 1em;
  margin-top: 0.8em;
  background-color: #587ef4;
  border: none;
  outline: none;
  color: #ffffff;
  padding: 0.6em 1.2em;
  border-radius: 0.3em;
  cursor: pointer;
}
.list {
  background-color: #ffffff;
  padding: 1.8em 1.2em;
  box-shadow: 0 0.6em 1.2em rgba(28, 0, 80, 0.06);
  border-radius: 0.6em;
}
.sublist-content {
  width: 100%;
  border-left: 0.3em solid #587ef4;
  margin-bottom: 0.6em;
  padding: 0.5em 1em;
  display: grid;
  grid-template-columns: 3fr 2fr 1fr 1fr;
}
.product {
  font-weight: 500;
  color: #363d55;
}
.amount {
  color: #414a67;
  margin-left: 20%;
}
.icons-container {
  width: 5em;
  margin: 1.2em;
  align-items: center;
}
.product-title {
  margin-bottom: 1em;
}
.hide {
  display: none;
}
.error {
  color: #ff465a;
}
.edit {
  margin-left: auto;
}
.edit,
.delete {
  background: transparent;
  cursor: pointer;
  margin-right: 1.5em;
  border: none;
  color: #587ef4;
}
@media screen and (max-width: 600px) {
  .wrapper {
    font-size: 14px;
  }
  .sub-container {
    grid-template-columns: 1fr;
    gap: 1em;
  }
}
Javascript:
Finally, we implement the functionality of the budget app. For this we use javascript. We do this in six steps:

Create initial references
Implement function to set budget
Function to disable Edit/Delete buttons
Create a function to modify list items
Create a function to create a list
Implement function to calculate expenses and balance.
**That’s all for this tutorial. If you face any issues while creating this code, you can download the source code by clicking on the ‘Download Code**
