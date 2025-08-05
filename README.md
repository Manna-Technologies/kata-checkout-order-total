# FE Challenge Guide and TDD Primer

Welcome to the Manna Technologies Frontend Katas. We are glad that you are here and excited by the prospect of having you join our team.

At Manna, we hold a few philosophies close to heart, one of said philosophies is TDD (Test Driven Development) which is usually coupled with Pair Programming. If you're scarcely familiar with TDD, please take the time to watch these videos, they should provide a good starting point:

- https://www.youtube.com/watch?v=Bq_oz7nCNUA
- https://www.youtube.com/watch?v=Jv2uxzhPFl4

## Katas Guide

Candidates are asked to complete one of four Katas (coding challenges) in a TDD style while paying special attention to the development cycle. To solve each kata you should go through the three phases of a TDD commit:

- **Red**: Write a failing test
- **Green**: Make the test pass
- **Refactor**: Find opportunities to refactor the code

We expect each test to be accompanied by at least 2–3 commits—one for the initial failing test, one for the implementation, and one for any refactoring (if applicable).

**Important**: Please structure your solution in a way that can be easily extended, as the second round of interviews will involve paired programming where we will extend your submitted code together.

The readme of each kata explains the problem thoroughly, however feel free to reach out to us at: moayed.mustafa@manna-technologies.com for further explanation.

## Submission

Make a GitHub repository for your submission and by the end of your attempt, send the repo to the following email: moayed.mustafa@manna-technologies.com

Your submission will be evaluated based on the following criteria:

- Ease of building the project and running tests
- Project organization and ease of understanding
- Naming conventions and clarity
- Clean code (as defined by the book of the same name) at the module/class and function/method level
- Minimal duplication (DRY)
- Idiomatic use of the programming language and associated tools
- Originality of solution (it must not be plagiarized)

## Clean Code Principles

As part of our evaluation, we look for adherence to clean code principles. Here are key concepts to keep in mind:

- **Meaningful Names**: Use intention-revealing names for variables, functions, and classes
- **Functions**: Keep functions small, focused on a single responsibility, and with minimal parameters
- **Comments**: Write code that is self-documenting; use comments sparingly and only when necessary
- **Formatting**: Maintain consistent indentation, spacing, and code organization
- **Error Handling**: Handle errors gracefully without obscuring the main logic
- **Testing**: Write tests that are clear, focused, and maintainable
- **SOLID Principles**: Follow object-oriented design principles for maintainable code
- **DRY (Don't Repeat Yourself)**: Avoid code duplication through proper abstraction

**Final note**: We care a lot about seeing your thought process. Even though we use AI in our day-to-day work, do not use AI for this challenge.

Good luck!

---

# Checkout Order Total Kata

You have been contracted to write part of a grocery point-of-sale system. Your job is to implement the business logic to calculate the pre-tax total price as items are scanned or entered at checkout.

Many items are sold at a per-unit price. For example, a can of soup sells for $1.89 each.

Some items are sold by weight. For example, 80% lean ground beef currently sells for $5.99 per pound. Bananas are currently $2.38 per pound.

Each week, some items are marked down. For example, the soup could be marked down 20 cents. In this case, it would sell for $1.69 during the week. Markdown prices must always be used in favor of the per-unit price during the sale. There are laws protecting the customer from false advertising.

Along with the markdowns, a set of specials are advertised each week. For example, the soup could be advertised as "buy one, get one free" or "buy two, get one half off" or "three cans for $5.00." Sometimes limits are placed on these specials. For example, "Buy two, get one free. Limit 6." Purchases not fitting the description of the special are sold at the per-unit price unless a markdown price has also been advertised.

## Requirements

- Your solution should have an API to configure the above kinds of prices, specials and markdowns. Instead of UPC or SKU codes, you may simply use strings such as "ground beef" or "soup" to describe what has been scanned or entered. **NOTE:** The term "API" simply refers to a collection of logical function calls exposed by your application. It does not necessarily imply something like a REST API.
- It should repeatedly accept a scanned item or item and weight through an API call. It must keep an accurate current total through the process.
- Clerks make mistakes. They need to be able to remove items from an order, immediately correcting the current total.
- You are not responsible for the display system or printing a receipt; only calculating the pre-tax total. The display system or receipt may query your code for the total.
- Your solution must not use a database. Everything will fit in memory.

## Use Cases

1. Accept a scanned item. The total should reflect an increase by the per-unit price after the scan. You will need a way to configure the prices of scannable items prior to being scanned.
2. Accept a scanned item and a weight. The total should reflect an increase of the price of the item for the given weight.
3. Support a markdown. A marked-down item will reflect the per-unit cost less the markdown when scanned. A weighted item with a markdown will reflect that reduction in cost per unit.
4. Support a special in the form of "Buy N items get M at %X off." For example, "Buy 1 get 1 free" or "Buy 2 get 1 half off."
5. Support a special in the form of "N for $X." For example, "3 for $5.00"
6. Support a limit on specials, for example, "buy 2 get 1 free, limit 6" would prevent getting a third free item.
7. Support removing a scanned item, keeping the total correct after possibly invalidating a special.
8. Support "Buy N, get M of equal or lesser value for %X off" on weighted items. For example, "Buy 2 pounds of ground beef, get 1 pound half off."
