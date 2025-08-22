module MyModule::Crowdfunding {

    use aptos_framework::signer;
    use aptos_framework::coin;
    use aptos_framework::aptos_coin::AptosCoin;

    /// Struct representing a crowdfunding project.
    struct Project has store, key {
        total_funds: u64,  // Total tokens raised for the project
        goal: u64,         // Funding goal of the project
    }

    /// Function to create a new project with a funding goal.
    public fun create_project(owner: &signer, goal: u64) {
        let project = Project {
            total_funds: 0,
            goal,
        };
        move_to(owner, project);
    }

    /// Function for users to support the project by contributing tokens.
    public fun contribute_to_project(contributor: &signer, project_owner: address, amount: u64) acquires Project {
        let project = borrow_global_mut<Project>(project_owner);

        // Transfer the contribution from the contributor to the project owner
        let contribution = coin::withdraw<AptosCoin>(contributor, amount);
        coin::deposit<AptosCoin>(project_owner, contribution);

        // Update the total funds raised
        project.total_funds = project.total_funds + amount;
    }
}
