# calendar
simple calendar website
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calendar</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Add your HTML content here -->
    <script src="scripts.js"></script>
</body>
</html>
<div id="calendar">
    <table>
        <thead>
            <tr>
                <th>Sun</th>
                <th>Mon</th>
                <th>Tue</th>
                <th>Wed</th>
                <th>Thu</th>
                <th>Fri</th>
                <th>Sat</th>
            </tr>
        </thead>
        <tbody id="calendar-body">
            <!-- Calendar days will be generated using JavaScript -->
        </tbody>
    </table>
</div>
body {
    font-family: Arial, sans-serif;
}

table {
    width: 100%;
    table-layout: fixed;
    border-collapse: collapse;
}

th, td {
    padding: 10px;
    text-align: center;
    border: 1px solid #ccc;
}

tr:nth-child(even) {
    background-color: #f2f2f2;
}
function generateCalendar(month, year) {
    const calendarBody = document.getElementById('calendar-body');
    const date = new Date(year, month);
    const firstDay = new Date(date.getFullYear(), date.getMonth(), 1).getDay();
    const daysInMonth = new Date(date.getFullYear(), date.getMonth() + 1, 0).getDate();

    calendarBody.innerHTML = '';

    let day = 1;
    for (let i = 0; i < 6; i++) {
        const row = document.createElement('tr');

        for (let j = 0; j < 7; j++) {
            const cell = document.createElement('td');

            if (i === 0 && j < firstDay || day > daysInMonth) {
                cell.innerHTML = '';
            } else {
                cell.innerHTML = day;
                day++;
            }

            row.appendChild(cell);
        }

        calendarBody.appendChild(row);

        if (day > daysInMonth) {
            break;
        }
    }
}

const currentDate = new Date();
generateCalendar(currentDate.getMonth(), currentDate.getFullYear());
