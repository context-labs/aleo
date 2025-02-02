[View code on GitHub](https://github.com/AleoHQ/aleo/website/src/tabs/rest/GetTransaction.js)

The `GetTransaction` component in this code is a React functional component that allows users to search for a specific transaction on the Aleo testnet blockchain by its transaction ID. The component uses the Ant Design library for its UI components and Axios for making API requests.

When a user enters a transaction ID in the search bar and submits the form, the `onSearch` function is called, which in turn calls the `tryRequest` function with the entered transaction ID as its argument. The `tryRequest` function sets the `transaction` state to `null` and makes an API request to the Aleo testnet blockchain using Axios. If the request is successful, the response data is stored in the `transaction` state as a formatted JSON string, and the `status` state is set to "success". If there's an error, the `status` state is set to "error".

The component renders a card with a form containing an input field for the transaction ID. The input field has a search button and allows clearing the input. The `onSearch` function is called when the search button is clicked or the user presses the Enter key. If the `transaction` state is not `null`, a new form is displayed below the input field, containing a read-only text area with the transaction data and a copy button to copy the transaction data to the clipboard.

Here's an example of how the `GetTransaction` component might be used in the larger project:

```jsx
import React from 'react';
import { GetTransaction } from './aleo/GetTransaction';

function App() {
  return (
    <div>
      <h1>Aleo Transaction Explorer</h1>
      <GetTransaction />
    </div>
  );
}

export default App;
```

In this example, the `GetTransaction` component is imported and used in the main `App` component, allowing users to search for transactions on the Aleo testnet blockchain.
## Questions: 
 1. **Question:** What is the purpose of the `GetTransaction` component and how does it fetch the transaction data?

   **Answer:** The `GetTransaction` component is a React functional component that allows users to search for a transaction by its ID. It fetches the transaction data by making an API call to `https://vm.aleo.org/api/testnet3/transaction/${id}` using the `axios` library.

2. **Question:** How does the `onSearch` function handle errors and what happens when the search bar is empty?

   **Answer:** The `onSearch` function calls the `tryRequest` function inside a try-catch block to handle any errors that may occur during the API call. If the search bar is empty, the `tryRequest` function resets the status to an empty string and does not make an API call.

3. **Question:** What is the purpose of the `transactionString` function and how is it used in the component?

   **Answer:** The `transactionString` function is used to convert the transaction data (if available) to a string format. It is used in the `Input.TextArea` component to display the transaction data and in the `CopyButton` component to provide the data to be copied.