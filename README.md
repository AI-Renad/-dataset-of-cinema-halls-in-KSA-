# Dataset of Cinema Halls in KSA

This repository contains a dataset of cinema halls in Saudi Arabia (KSA) with ratings, review counts, and comments. In this repository, we will learn how to load the dataset into MySQL and perform different SQL queries to analyze the data.

## 🧠 Let's Learn How to Load a CSV File into MySQL
Step 1: Create or Select a Database Open MySQL Workbench. Create a new database or select an existing one.
<img width="295" alt="Screenshot 2025-02-11 at 11 23 14 AM" src="https://github.com/user-attachments/assets/9d6205c8-4091-4732-a308-ee85eb4f0505" />

Step 2: Use the Table Data Import Wizard Right-click on the database in the Navigator panel. Select Table Data Import Wizard from the context menu.

<img width="767" alt="Screenshot 2025-02-11 at 11 23 42 AM" src="https://github.com/user-attachments/assets/44d380ef-b209-4bc4-a106-ead84c0742c5" />

Step 3: Select the CSV File In the wizard, browse to and select the CSV file you want to import. Click Next.

### Get the total number of cinema halls in a specific location:
```
use company;
SELECT COUNT(*) AS total_halls
FROM cinema_halls
WHERE location LIKE '%Riyadh%';
```
<img width="584" alt="Screenshot 2025-02-11 at 11 37 56 AM" src="https://github.com/user-attachments/assets/76b81d9e-911c-4939-b338-36dfd5baef54" />

### Get the average rating of all cinema halls:
```
SELECT AVG(rating) AS average_rating
FROM cinema_halls;
```
<img width="466" alt="Screenshot 2025-02-11 at 11 38 35 AM" src="https://github.com/user-attachments/assets/22415c2e-a0bd-4587-8d5e-edb989d5ddcd" />

### Get all cinema halls with a rating higher than 4.0:
```
SELECT * FROM cinema_halls
WHERE rating > 4.0;
```
<img width="713" alt="Screenshot 2025-02-11 at 11 40 37 AM" src="https://github.com/user-attachments/assets/cd88a41c-3a80-4063-9349-70cdfce430d3" />

### Get the top 5 cinema halls with the highest number of reviews:
```
SELECT name, best_comment
FROM cinema_halls
WHERE best_comment LIKE '%Sound%';
```
<img width="575" alt="Screenshot 2025-02-11 at 11 41 34 AM" src="https://github.com/user-attachments/assets/c492ff33-a49d-4ca5-88d0-33a0d4a42bd7" />

### Get the lowest-rated cinema halls (with a limit):
```
SELECT name, rating
FROM cinema_halls
ORDER BY rating ASC
LIMIT 5;
```
<img width="459" alt="Screenshot 2025-02-11 at 11 44 33 AM" src="https://github.com/user-attachments/assets/1ac1108c-666d-4f15-8273-1a2dfaa16b68" />


### Get the average rating per genre of cinema halls:
```
SELECT genre, AVG(rating) AS average_rating
FROM cinema_halls
GROUP BY genre;
```
<img width="499" alt="Screenshot 2025-02-11 at 11 45 12 AM" src="https://github.com/user-attachments/assets/0daeff36-02f5-4ce3-9e3e-114b160122cf" />


### List all distinct genres available in the cinema halls:
```
SELECT DISTINCT genre FROM cinema_halls;
```
<img width="541" alt="Screenshot 2025-02-11 at 11 45 48 AM" src="https://github.com/user-attachments/assets/62cd01a2-4f62-4ce7-b797-0bc653b28bd4" />


### Get the cinema hall with the most reviews:
```
SELECT name, review_count
FROM cinema_halls
ORDER BY review_count DESC
LIMIT 1;
```
<img width="456" alt="Screenshot 2025-02-11 at 11 48 34 AM" src="https://github.com/user-attachments/assets/a9c44fcf-c3bd-401e-9287-1df1f0c82ec8" />


### to Calculate Average Rating for a Cinema Hall by Name:
```
DELIMITER $$
CREATE FUNCTION GetAvgRating(cinema_name VARCHAR(255))
RETURNS DECIMAL(3,2)
DETERMINISTIC
BEGIN
    DECLARE avg_rating DECIMAL(3,2);
    SELECT AVG(rating) INTO avg_rating
    FROM cinema_halls
    WHERE name = cinema_name;
    RETURN avg_rating;
END$$
DELIMITER ;

```
<img width="519" alt="Screenshot 2025-02-11 at 11 50 19 AM" src="https://github.com/user-attachments/assets/fb8924af-9692-46a0-9013-38742afd9f00" />


## Conclusion

In this repository, we've demonstrated how to load a dataset of cinema halls into MySQL and execute various SQL queries to analyze the data. From retrieving the total number of halls in a specific location to calculating the average rating by cinema name, these queries serve as examples of how you can interact with and analyze your own cinema data.
