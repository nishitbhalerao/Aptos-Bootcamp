
# Crowdfunding Module (Move on Aptos)

This module implements a **basic crowdfunding system** on the Aptos blockchain using the Move programming language.
It allows project owners to create crowdfunding projects with funding goals and lets contributors support them with Aptos tokens.

---

## 📌 Features

* **Create Project**: A project owner can start a crowdfunding project with a funding goal.
* **Contribute**: Users can contribute Aptos tokens (`AptosCoin`) to support a project.
* **Fund Tracking**: The total funds raised for each project are tracked on-chain.

---

## 📂 Module Structure

```move
module MyModule::Crowdfunding {
    struct Project {
        total_funds: u64,  // Total tokens raised
        goal: u64,         // Target funding goal
    }

    public fun create_project(owner: &signer, goal: u64) { ... }
    public fun contribute_to_project(contributor: &signer, project_owner: address, amount: u64) { ... }
}
```

---

## ⚙️ Functions

### `create_project(owner: &signer, goal: u64)`

* Creates a new project with the specified funding goal.
* Stores the project under the owner's account.

**Parameters:**

* `owner`: The account creating the project.
* `goal`: The funding goal (in Aptos tokens).

---

### `contribute_to_project(contributor: &signer, project_owner: address, amount: u64)`

* Allows a user to contribute tokens to a project.
* Tokens are transferred from the contributor to the project owner.
* Updates the project’s total funds raised.

**Parameters:**

* `contributor`: The account making the contribution.
* `project_owner`: The address of the project creator.
* `amount`: Number of Aptos tokens to contribute.

---

## 🚀 Example Usage

### 1. Create a Project

```move
// Alice creates a crowdfunding project with a goal of 1000 AptosCoins
Crowdfunding::create_project(&alice, 1000);
```

### 2. Contribute to a Project

```move
// Bob contributes 200 AptosCoins to Alice's project
Crowdfunding::contribute_to_project(&bob, @alice, 200);
```

---

## 🔒 Security Notes

* Only the **project owner** can host one `Project` resource at their address.
* Contributors must hold sufficient Aptos tokens in their account.
* Contributions are **directly transferred** to the project owner’s account.

---

## 📜 License

This module is provided as a sample for educational and development purposes.
You may modify and use it in your own Aptos blockchain projects.

---

