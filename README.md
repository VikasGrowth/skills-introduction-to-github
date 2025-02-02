<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Zoho CRM Form</title>
</head>
<body>
    <h2>Submit Data to Zoho CRM</h2>
    <form id="zohoForm">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>

        <button type="submit">Submit</button>
    </form>

    <script>
        document.getElementById("zohoForm").addEventListener("submit", async function(event) {
            event.preventDefault();

            const formData = {
                data: [{
                    First_Name: document.getElementById("name").value,
                    Email: document.getElementById("email").value
                }]
            };

            const response = await fetch("https://www.zohoapis.com/crm/v2/Leads", {
                method: "POST",
                headers: {
                    "Authorization": "Zoho-oauthtoken YOUR_ACCESS_TOKEN",
                    "Content-Type": "application/json"
                },
                body: JSON.stringify(formData)
            });

            if (response.ok) {
                alert("Data submitted successfully!");
            } else {
                alert("Error submitting data.");
            }
        });
    </script>
</body>
</html>
