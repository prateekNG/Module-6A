### Problem 1: Developer Team Selector

---

**Problem Description**:

You're managing a tech project that requires assembling a specialized team of developers with particular skill sets and availability. Your objective is to build a data report that shows only specific details for each selected team member.

You have an array of `developer` objects, each with the following properties:

- `name`: The developer’s name (string).
- `age`: The developer’s age (number).
- `skills`: An array of skills (strings) that the developer possesses.
- `experience`: An object with properties `{ years: number, seniority: string }` detailing the developer's experience.
- `availability`: A boolean indicating if the developer is currently available for new projects.

**Requirements**:

1. Write a function named `buildTeamReport` that:
   - Takes two parameters:
     - An array of developers.
     - A minimum experience level in years.
   - Uses **object destructuring** to access the nested properties of each developer (name, age, experience, skills).
   - Uses **rest/spread** to separate certain information, specifically focusing on selecting developers who:
     - Are currently available.
     - Have experience greater than or equal to the given minimum experience.
2. Returns an array of team objects containing:
   - The developer's `name`.
   - A `summary` object containing:
     - Their years of experience (`experience.years`),
     - Primary skill (first skill in the skills array).
   - All other skills as a `secondarySkills` array.

**Example**:

Given the following array of developers:

```javascript
const developers = [
    {
        name: "Alice",
        age: 25,
        skills: ["JavaScript", "React", "Node.js"],
        experience: { years: 3, seniority: "mid" },
        availability: true
    },
    {
        name: "Bob",
        age: 30,
        skills: ["HTML", "CSS", "JavaScript"],
        experience: { years: 2, seniority: "junior" },
        availability: true
    },
    {
        name: "Eva",
        age: 32,
        skills: ["JavaScript", "React", "GraphQL", "TypeScript"],
        experience: { years: 5, seniority: "senior" },
        availability: true
    }
];
```

Calling `buildTeamReport(developers, 3)` should return:

```javascript
[
    {
        name: "Alice",
        summary: {
            years: 3,
            primarySkill: "JavaScript"
        },
        secondarySkills: ["React", "Node.js"]
    },
    {
        name: "Eva",
        summary: {
            years: 5,
            primarySkill: "JavaScript"
        },
        secondarySkills: ["React", "GraphQL", "TypeScript"]
    }
];
```

**Hints**:
1. Use destructuring to access `name`, `experience.years`, and the first skill from `skills`.
2. Use the rest operator to capture additional skills after the primary skill.

---

### Learning Objectives / Skills Practiced:

1. **Object Destructuring**: Practice accessing nested properties (e.g., `experience.years`) directly within functions.
2. **Rest/Spread Operators**: Learn to separate specific items in arrays (like primary vs. secondary skills) using spread/rest.
3. **Higher-Order Functions**: Apply `filter` and `map` to transform and filter data according to specific criteria.
4. **Functional Data Reshaping**: Gain practice in reshaping data, useful in real-world scenarios where objects often need to be restructured based on requirements.
