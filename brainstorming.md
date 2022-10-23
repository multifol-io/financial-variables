# An Example Scenario

A tool-writer builds a tool for users to more easily model their financial sitution to follow the Prioritizing Investments bogleheads wiki: https://bogle.tools/saving

They publish their source code: https://github.com/rrelyea/bogle.tools-saving

Initially, they hard code many of the tax constants:

- IRA Allowed Contribution of $6,000 and catch-up amount of $1,000: https://github.com/rrelyea/bogle.tools-saving/blob/main/src/Shared/IRA.cs#L15

However, each year this will need to be updated.

## How it could work

The tool-writer defines a set of constants they need.

- IRS-IRA-ContributionLimit
- IRA-401k-ContributionLimit
- IRS-401k-CatchUpContribtionLimit

At runtime, or periodically, they would update the numbers their tool used by fetching those values:

- IRS-IRA-ContributionLimit: $6,500
- IRA-401k-ContributionLimit: $22,500
- IRS-401k-CatchUpContribtionLimit: $7,500

### Requirement: Naming of Values

We already see we need a naming scheme for these values.

### Requirement: Fetching latest or specific years

I'd imagine there is a way you could lookup the latest values, as well as a specific years.
