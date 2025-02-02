[View code on GitHub](https://github.com/AleoHQ/aleo/rust/src/program/helpers/records.rs)

The `RecordFinder` struct in this code serves as a helper for finding records on the Aleo blockchain during program development. It provides methods to search for records with specific amounts and fees, as well as to find unspent records on the chain. The struct takes an `AleoAPIClient` as a parameter, which is used to interact with the Aleo network.

The `find_amount_and_fee_records` method takes an amount, fee, and private key as input and returns two records for the transfer amount and fee, respectively. This can be used to find records needed for a transaction. For example:

```rust
let (amount_record, fee_record) = record_finder.find_amount_and_fee_records(amount, fee, private_key)?;
```

The `find_one_record` method takes a private key and an amount as input and returns a single record with a value equal to or greater than the specified amount. This can be useful for finding a record with a specific value.

The `find_record_amounts` method takes a vector of amounts and a private key as input and attempts to resolve records with specific values. If successful, it returns a vector of records with values equal to or greater than the specified amounts.

The `find_unspent_records_on_chain` method takes optional amounts, an optional maximum value, and a private key as input and returns a vector of unspent records on the chain. This method is used internally by the other methods to find records based on the given criteria.

Overall, the `RecordFinder` struct provides a convenient way to search for records on the Aleo blockchain, which can be useful during program development and testing.
## Questions: 
 1. **Question**: What is the purpose of the `RecordFinder` struct and how does it interact with the AleoAPIClient?
   **Answer**: The `RecordFinder` struct is a helper structure for finding records on the Aleo blockchain during program development. It interacts with the AleoAPIClient to fetch unspent records and perform operations such as finding records with specific amounts or resolving records for a transfer amount and fee.

2. **Question**: How does the `find_amount_and_fee_records` function work and what are its inputs and outputs?
   **Answer**: The `find_amount_and_fee_records` function takes an amount, a fee, and a private key as inputs. It attempts to find two records on the Aleo blockchain with amounts equal to or greater than the specified amount and fee. If successful, it returns a tuple containing the two records; otherwise, it returns an error indicating insufficient funds.

3. **Question**: What is the purpose of the `find_unspent_records_on_chain` function and what are its inputs and outputs?
   **Answer**: The `find_unspent_records_on_chain` function is used to find unspent records on the Aleo blockchain based on the specified criteria. It takes an optional list of amounts, an optional maximum microcredits value, and a private key as inputs. The function returns a vector of decrypted records that match the given criteria, or an error if the records cannot be found or decrypted.