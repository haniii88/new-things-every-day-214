```javascript
function dailyLog214() {
  const employees = [
    { name: "Alex", present: 20, absent: 1, late: 2 },
    { name: "Sarah", present: 18, absent: 3, late: 1 },
    { name: "Michael", present: 21, absent: 0, late: 0 },
    { name: "Emma", present: 16, absent: 5, late: 3 },
    { name: "Daniel", present: 19, absent: 2, late: 1 },
  ];

  const attendanceRate = employee => {
    const total = employee.present + employee.absent;

    return total === 0
      ? 0
      : (employee.present / total) * 100;
  };

  const totalPresent = employees.reduce(
    (sum, employee) => sum + employee.present,
    0
  );

  const totalAbsent = employees.reduce(
    (sum, employee) => sum + employee.absent,
    0
  );

  const needsReview = employees.filter(
    employee => attendanceRate(employee) < 85
  );

  console.log("=== Employee Attendance Report ===");
  console.log(`Employees: ${employees.length}`);
  console.log(`Total Present Days: ${totalPresent}`);
  console.log(`Total Absent Days: ${totalAbsent}`);

  console.log("\n=== Individual Attendance ===");

  employees.forEach(employee => {
    console.log(
      `${employee.name}: ${attendanceRate(employee).toFixed(1)}% attendance, ` +
      `${employee.late} late arrivals`
    );
  });

  console.log(`\nEmployees Below 85%: ${needsReview.length}`);

  needsReview.forEach(employee => {
    console.log(`⚠️ Follow-up recommended: ${employee.name}`);
  });
}

dailyLog214();
```
