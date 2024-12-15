This a personal project use postresql to query the data set, created relationship explore the data to derive meaningful insight. Then use Power BI to visualise and present my findings 
FROM public.donation_data

--A)How much is the total donation?
SELECT sum (donation) AS Total_Donation
FROM public.donation_data

--B) What is the total donation by gender?

SELECT gender,sum (donation) AS Total_Donation
FROM public.donation_data
GROUP BY gender

--C)Show the total donation and number of donations  by gender
SELECT gender,sum (donation) AS Total_Donation,COUNT (gender) Number_Of_Gender
FROM public.donation_data
GROUP BY gender

--D)Total donation made by frequency of donation
SELECT sum (donation) AS Total_Donation,donation_frequency AS Frequency_Of_Donation
FROM public.donation_data
JOIN public.donor_data
ON public.donor_data.id=public.donation_data.id
GROUP BY donation_frequency

--E)Total donation and number of donation by Job field
SELECT job_field,sum (donation) AS Total_DonationBy_JobField
FROM public.donation_data
GROUP BY job_field

--F)Total donation and number of donations above $200
SELECT sum (donation) AS Total_Donation, COUNT (donation) 
FROM public.donation_data
WHERE donation > 200

--G)Total donation and number of donations below $200
SELECT sum (donation) AS Total_Donation, COUNT (donation) 
FROM public.donation_data
WHERE donation < 200

--H)Which top 10 states contributes the highest donations
SELECT sum (donation) AS Total_Donation, COUNT (donation) 
FROM public.donation_data
WHERE donation < 200

--I)Which top 10 states contributes the highest donations
SELECT state,donation
FROM public.donation_data
ORDER BY donation desc
LIMIT 10

--J) Which top 10 states contributes the least donations
SELECT state,donation
FROM public.donation_data
ORDER BY donation asc
LIMIT 10
![image](https://github.com/user-attachments/assets/85876a85-cf80-474d-9dd3-55f1915f1505)
![image](https://github.com/user-attachments/assets/65cf8957-e347-4d72-a383-42efb9777e46)


