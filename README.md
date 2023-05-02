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
import Results from "../Results";

test("renders correctly with no pets", () => {
  const { asFragment } = render(<Results pets={[]} />);
  expect(asFragment()).toMatchSnapshot();
});

// sample
const pets = [
  {
    id: 1,
    name: "Luna",
    animal: "dog",
    city: "Seattle",
    state: "WA",
    description:
      "Luna is actually the most adorable dog in the world. Her hobbies include yelling at squirrels, aggressively napping on her owners' laps, and asking to be fed two hours before IT'S DAMN WELL TIME LUNA. Luna is beloved by her puppy parents and lazily resides currently in Seattle, Washington.",
    breed: "Havanese",
    images: [
      "http://pets-images.dev-apis.com/pets/dog25.jpg",
      "http://pets-images.dev-apis.com/pets/dog26.jpg",
      "http://pets-images.dev-apis.com/pets/dog27.jpg",
      "http://pets-images.dev-apis.com/pets/dog28.jpg",
      "http://pets-images.dev-apis.com/pets/dog29.jpg"
    ]
  },
  {
    id: 2,
    name: "Charisse",
    animal: "rabbit",
    city: "Lexington",
    state: "KY",
    description:
      "Maecenas leo odio, condimentum id, luctus nec, molestie sed, justo. Pellentesque viverra pede ac diam. Cras pellentesque volutpat dui.\n\nMaecenas tristique, est et tempus semper, est quam pharetra magna, ac consequat metus sapien ut nunc. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Mauris viverra diam vitae quam. Suspendisse potenti.",
    breed: "Havanese",
    images: ["http://pets-images.dev-apis.com/pets/rabbit0.jpg"]
  },
  {
    id: 3,
    name: "Maitilde",
    animal: "rabbit",
    city: "Dallas",
    state: "TX",
    description:
      "Duis consequat dui nec nisi volutpat eleifend. Donec ut dolor. Morbi vel lectus in quam fringilla rhoncus.\n\nMauris enim leo, rhoncus sed, vestibulum sit amet, cursus id, turpis. Integer aliquet, massa id lobortis convallis, tortor risus dapibus augue, vel accumsan tellus nisi eu orci. Mauris lacinia sapien quis libero.\n\nNullam sit amet turpis elementum ligula vehicula consequat. Morbi a ipsum. Integer a nibh.",
    breed: "Lab",
    images: ["http://pets-images.dev-apis.com/pets/rabbit1.jpg"]
  },
  {
    id: 4,
    name: "Natalina",
    animal: "rabbit",
    city: "Tampa",
    state: "FL",
    description:
      "Mauris enim leo, rhoncus sed, vestibulum sit amet, cursus id, turpis. Integer aliquet, massa id lobortis convallis, tortor risus dapibus augue, vel accumsan tellus nisi eu orci. Mauris lacinia sapien quis libero.\n\nNullam sit amet turpis elementum ligula vehicula consequat. Morbi a ipsum. Integer a nibh.\n\nIn quis justo. Maecenas rhoncus aliquam lacus. Morbi quis tortor id nulla ultrices aliquet.",
    breed: "Lab",
    images: ["http://pets-images.dev-apis.com/pets/rabbit2.jpg"]
  },
  {
    id: 5,
    name: "Michail",
    animal: "reptile",
    city: "Tuscaloosa",
    state: "AL",
    description:
      "Nulla ut erat id mauris vulputate elementum. Nullam varius. Nulla facilisi.\n\nCras non velit nec nisi vulputate nonummy. Maecenas tincidunt lacus at velit. Vivamus vel nulla eget eros elementum pellentesque.\n\nQuisque porta volutpat erat. Quisque erat eros, viverra eget, congue eget, semper rutrum, nulla. Nunc purus.",
    breed: "Havanese",
    images: ["http://pets-images.dev-apis.com/pets/reptile1.jpg"]
  },
  {
    id: 6,
    name: "Gizela",
    animal: "bird",
    city: "Carol Stream",
    state: "IL",
    description:
      "Nullam sit amet turpis elementum ligula vehicula consequat. Morbi a ipsum. Integer a nibh.\n\nIn quis justo. Maecenas rhoncus aliquam lacus. Morbi quis tortor id nulla ultrices aliquet.",
    breed: "Havanese",
    images: ["http://pets-images.dev-apis.com/pets/bird2.jpg"]
  },
  {
    id: 7,
    name: "Laughton",
    animal: "reptile",
    city: "Bridgeport",
    state: "CT",
    description:
      "Cras mi pede, malesuada in, imperdiet et, commodo vulputate, justo. In blandit ultrices enim. Lorem ipsum dolor sit amet, consectetuer adipiscing elit.",
    breed: "Havanese",
    images: ["http://pets-images.dev-apis.com/pets/reptile2.jpg"]
  },
  {
    id: 8,
    name: "Si",
    animal: "dog",
    city: "Charlotte",
    state: "NC",
    description:
      "Praesent id massa id nisl venenatis lacinia. Aenean sit amet justo. Morbi ut odio.",
    breed: "Lab",
    images: ["http://pets-images.dev-apis.com/pets/dog0.jpg"]
  },
  {
    id: 9,
    name: "Lyda",
    animal: "rabbit",
    city: "Springfield",
    state: "IL",
    description:
      "Curabitur gravida nisi at nibh. In hac habitasse platea dictumst. Aliquam augue quam, sollicitudin vitae, consectetuer eget, rutrum at, lorem.\n\nInteger tincidunt ante vel ipsum. Praesent blandit lacinia erat. Vestibulum sed magna at nunc commodo placerat.",
    breed: "Lab",
    images: ["http://pets-images.dev-apis.com/pets/rabbit3.jpg"]
  },
  {
    id: 10,
    name: "Jackquelin",
    animal: "dog",
    city: "Tucson",
    state: "AZ",
    description:
      "Donec diam neque, vestibulum eget, vulputate ut, ultrices vel, augue. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Donec pharetra, magna vestibulum aliquet ultrices, erat tortor sollicitudin mi, sit amet lobortis sapien sapien non mi. Integer ac neque.",
    breed: "Lab",
    images: ["http://pets-images.dev-apis.com/pets/dog1.jpg"]
  }
];

test("renders correctly with some pets", () => {
  const { asFragment } = render(
    <StaticRouter>
      <Results pets={pets} />
    </StaticRouter>
  );
  expect(asFragment()).toMatchSnapshot();
});
```

This test imports the `render` and `screen` functions from `@testing-library/react ` and the `Vitest` class from `vitest`.
It then renders the `PetList` component using Vitest's `render` method and checks that the names of three pets are present in the rendered output.

## Coverage Reports

To generate a coverage report for the tests, run `npm test -- --coverage`. This will run the tests and generate a report in the `coverage` directory.

## Conclusion

Vitest makes it easy to write and run tests for your React applications. With Vitest, you can ensure that your application is functioning as expected and catch bugs before they make it to production.
