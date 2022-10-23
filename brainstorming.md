# An Example Scenario

A tool writer builds a tool for users to more easily model their financial sitution to follow the Prioritizing Investments bogleheads wiki: https://bogle.tools/saving

They publish their source code: https://github.com/rrelyea/bogle.tools-saving

Initially, they hard code many of the tax constants:

- IRA Allowed Contribution of $6,000 and catch-up amount of $1,000: https://github.com/rrelyea/bogle.tools-saving/blob/main/src/Shared/IRA.cs#L15

However, each year this will need to be updated.