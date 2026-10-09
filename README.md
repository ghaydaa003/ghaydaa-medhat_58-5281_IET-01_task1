# Task 1 - Inconsistencies and duplicates

**Name:** Ghaydaa Medhat Mohamed Amer
**ID:** 58-5281
**Major:** IET

## Cleaning explanation

The file had 39 rows and messy values. Faculty, club and city were written in different ways, like "Alex" and "Alexandria", "El Giza" and "Giza", "Pharma" and "Pharmacy", "Soccer" and "Football", "Debating" and "Debate", "Chess Club" and "Chess". I made everything lower case and removed spaces, then used a dictionary to turn each version into one allowed name, for example Media Engineering and Technology became MET. I checked with an assert that only the allowed values are left. Names had extra spaces and mixed capitals, so I fixed them to one style, and emails were trimmed and made lower case. The fee column had yes, Y, 1, no, N and so on, so I changed it to True and False. The dates had two formats, and in the slash one the first number is the day because it goes up to 18. I parsed each format separately into one datetime column. Then I removed 3 exact duplicate rows (36 left), and then 4 rows where the same student signed up again for the same club (32 left). I kept the latest one because students came back to mark the fee as paid, so the last row is the newest. The order matters: if I removed duplicates before fixing the clubs, I would only find 2 of those 4, because "Chess" and "Chess Club" look like different clubs. Two different students are both called Mohamed Adel, so I matched using student_id and club, not the name, and they stayed separate.
