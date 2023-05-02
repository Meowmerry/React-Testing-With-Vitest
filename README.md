# React Testing with Vitest for Adopt Me Project

This README will guide you through the process of setting up and running tests for the
Adopt Me Project using Vitest.

## Testing with Vitest

`Vitest` is a test runner made by the fine folks who make Vite (as well as Vue.) The idea behind Vitest is that you already have a complete build pipeline for making an app, why should that pipeline be any different for test? It shouldn't; you want your testing environment to look as much like your app environment as possible.

They designed it to be a drop-in replacement for `Jest : https://jestjs.io/` which is what I have taught for this course since the beginning. Jest is great and still a very viable tool to use for testing, even with Vite. We're just going to use Vitest because 1. we don't have to do any more configuration and 2. 100% of what you will learn in here is going to be useful if you use Jest. Win-win. If you want to learn Jest specifically

## Prerequisites

Before you get started, make sure you have the following installed on your system:

- Node.js (version 12 or higher)
- npm (version 6 or higher)
- Adopt Me Project (Clone the repository from GitHub and install dependencies)

## Installation

Let's get going Run
`npm install -D vitest@0.24.3 @testing-library/react@13.4.0 happy-dom@7.6.0`

Navigate to the root directory of the Adopt Me Project in your terminal.
Run npm install --save-dev @testing-library/react vitest.

## Running the Tests

- In the root directory of the project, run npm test.
- The test runner will launch and execute all tests found in the **tests** directory.

## Writing Tests

Tests for the Adopt Me Project are located in the **tests** directory. Each test file is named according to the component or feature being tested and is suffixed with
`.test.tsx.`

When writing tests, be sure to import the necessary functions and components from the `@testing-library/react and vitest packages.`

Here's an example of a basic test for the PetList component:

```js
import { expect, test } from "vitest";
import { render } from "@testing-library/react";
import { StaticRouter } from "react-router-dom/server";
import Pet from "../Pet";

test("displays a default thumbnail", async () => {
  const pet = render(
    // Use StaticRouter because in Pet.jsx use Link "react-router-dom";
    <StaticRouter>
      <Pet />
    </StaticRouter>
  );

  const petThumbnail = await pet.findByTestId("thumbnail");
  expect(petThumbnail.src).toContain("none.jpg");
  pet.unmount(); // clean up after run test
});

test("displays a non-default thumbnail", async () => {
  const pet = render(
    <StaticRouter>
      <Pet images={["1.jpg", "2.jpg", "3.jpg"]} />
    </StaticRouter>
  );

  const petThumbnail = await pet.findByTestId("thumbnail");
  expect(petThumbnail.src).toContain("1.jpg");
  pet.unmount();
});
```

This test imports the `render` and `screen` functions from `@testing-library/react ` and the `Vitest` class from `vitest`.
It then renders the `PetList` component using Vitest's `render` method and checks that the names of three pets are present in the rendered output.

## Coverage Reports

To generate a coverage report for the tests, run `npm test -- --coverage`. This will run the tests and generate a report in the `coverage` directory.

## Conclusion

Vitest makes it easy to write and run tests for your React applications. With Vitest, you can ensure that your application is functioning as expected and catch bugs before they make it to production.
