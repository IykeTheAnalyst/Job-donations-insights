SELECT *
FROM donationhubdb.donation_data;

-- The mean donation amount
SELECT AVG(donation) AS mean_donation
FROM donation_data;

-- Which State has the highest number of donators. = Califronia has the highest number of 113 donators
SELECT state, COUNT(*) AS num_donators
FROM donation_data
GROUP BY state
ORDER BY num_donators DESC
LIMIT 1;

-- What is the average donation amount by Gender 
SELECT gender, AVG(donation) AS average_donation
FROM donation_data
GROUP BY gender;

-- Which jobfield has the highest donation amount
SELECT job_field, SUM(donation) AS total_donations
FROM donation_data
GROUP BY job_field
ORDER BY total_donations DESC
LIMIT 1;

-- What is the distribution of donation amount by state 
SELECT state, COUNT(*) AS num_donations, SUM(donation) AS total_donations, AVG(donation) AS average_donation
FROM donation_data
GROUP BY state
ORDER BY total_donations DESC;

-- Which shirt size are more commonly requested 
SELECT shirt_size, COUNT(*) AS num_requests
FROM donation_data
GROUP BY shirt_size
ORDER BY num_requests DESC;

-- What is the correlation between donation amount and shirt sizes
SELECT shirt_size, AVG(donation) AS average_donation
FROM donation_data
GROUP BY shirt_size
ORDER BY average_donation DESC;

-- What is the percentage of donors who request shirt sizes
SELECT 
    (COUNT(DISTINCT CASE WHEN shirt_size IS NOT NULL THEN id END) / COUNT(DISTINCT id)) * 100 AS percentage_with_shirt_size
FROM donation_data;

-- Which jobfield are most likely to request shirt sizes 
SELECT job_field, 
       COUNT(DISTINCT CASE WHEN shirt_size IS NOT NULL THEN id END) AS num_with_shirt_size,
       COUNT(DISTINCT id) AS total_donors,
       (COUNT(DISTINCT CASE WHEN shirt_size IS NOT NULL THEN id END) / COUNT(DISTINCT id)) * 100 AS percentage_with_shirt_size
FROM donation_data
GROUP BY job_field
ORDER BY percentage_with_shirt_size DESC;

-- What is the average donation amount by age group 
SELECT 
    CASE 
        WHEN age BETWEEN 18 AND 24 THEN '18-24'
        WHEN age BETWEEN 25 AND 34 THEN '25-34'
        WHEN age BETWEEN 35 AND 44 THEN '35-44'
        WHEN age BETWEEN 45 AND 54 THEN '45-54'
        WHEN age BETWEEN 55 AND 64 THEN '55-64'
        WHEN age BETWEEN 60 AND 74 THEN '60-74'        ELSE '65+' 
    END AS age_group,
    AVG(donation) AS average_donation
FROM donation_data
GROUP BY age_group
ORDER BY age_group;

-- Which state has the highest Percentage of repeated donators.
SELECT state,
       (COUNT(DISTINCT CASE WHEN donation_count > 1 THEN id END) / COUNT(DISTINCT id)) * 100 AS percentage_repeated_donors
FROM (
    SELECT id, state, COUNT(*) AS donation_count
    FROM donation_data
    GROUP BY id, state
) AS donor_counts
GROUP BY state
ORDER BY percentage_repeated_donors DESC
LIMIT 1;

-- What is the distribution of amount by jobfield
SELECT job_field, 
       COUNT(*) AS num_donations,
       SUM(donation) AS total_donations,
       AVG(donation) AS average_donation,
       MIN(donation) AS min_donation,
       MAX(donation) AS max_donation
FROM donation_data
GROUP BY job_field
ORDER BY total_donations DESC;

-- What shirt size are associated to the average donation amount
SELECT shirt_size, AVG(donation) AS average_donation
FROM donation_data
GROUP BY shirt_size
ORDER BY average_donation DESC;

-- What is the correlation between donation amount and jobfield
SELECT job_field, AVG(donation) AS average_donation
FROM donation_data
GROUP BY job_field
ORDER BY average_donation DESC;

-- What is the percentage of donor who donate more than $1000
SELECT 
    (COUNT(DISTINCT CASE WHEN donation > 1000 THEN id END) / COUNT(DISTINCT id)) * 100 AS percentage_donors_above_1000
FROM donation_data;


-- What are the top 5 job fields with the highest average donation amount?
SELECT job_field, AVG(donation) AS average_donation
FROM donation_data
GROUP BY job_field
ORDER BY average_donation DESC
LIMIT 5;

















