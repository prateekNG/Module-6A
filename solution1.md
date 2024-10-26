
### Solution:

```javascript
function buildTeamReport(developers, minExperience) {
    return developers
        .filter(({ experience: { years }, availability }) => years >= minExperience && availability)
        .map(({ name, skills: [primarySkill, ...secondarySkills], experience: { years } }) => ({
            name,
            summary: {
                years,
                primarySkill
            },
            secondarySkills
        }));
}

// Test the function with sample data
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

console.log(buildTeamReport(developers, 3));
// Expected output:
// [
//     {
//         name: "Alice",
//         summary: {
//             years: 3,
//             primarySkill: "JavaScript"
//         },
//         secondarySkills: ["React", "Node.js"]
//     },
//     {
//         name: "Eva",
//         summary: {
//             years: 5,
//             primarySkill: "JavaScript"
//         },
//         secondarySkills: ["React", "GraphQL", "TypeScript"]
//     }
// ];
```
