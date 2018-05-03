# group3
# GroupProject

-- 1. Which town has the most companies?(employment opportunities)
```SQL
SELECT
libgeo,
e14tst
FROM datasets.french_employment_base_etablissement_par_tranche_effectif
Order by e14tst DESC

Answer: Paris
```
group3/1.png

-- 2. What is the average number of firms in a town?
```SQL
SELECT avg(e14tst)
FROM datasets.french_employment_base_etablissement_par_tranche_effectif

Answer: 123
```

-- 3. What is the French town’s mean net salary? (economy condition)
```SQL
SELECT
AVG(snhm14)
FROM datasets.french_employment_net_salary_per_town_categories
```

-- 4. Which town has the most mean net salary for middle manager?
```SQL
SELECT
libgeo,
snhmp14
FROM datasets.french_employment_net_salary_per_town_categories
Order by snhmp14 DESC
```

-- 5. Which age range makes the most money in the largest city (Paris)? 
```SQL
Both male and female:
SELECT libgeo, snhmf1814, SNHMf2614, SNHMf5014, snhmh1814, SNHMH2614, SNHMH5014
from datasets.french_employment_net_salary_per_town_categories
where libgeo = 'Paris'
```

-- 6. What is the gender gap between Female and Male Net Salary/ Hr of Executives by Total Firms in Town? 
SNHMFC14 : mean net salary per hour for feminin executive
SNHMHC14 : mean net salary per hour for masculin executive

-- What is the relationship between Total_Firms and Female Executive Salaries in Towns?
```SQL
SELECT firms.libgeo,salary.snhmfc14 as fem_exec, firms.e14tst as Total_Firms
FROM datasets.french_employment_base_etablissement_par_tranche_effectif firms
JOIN datasets.french_employment_net_salary_per_town_categories salary
ON firms.libgeo = salary.libgeo
order by total_firms DESC
```

-- What is the relationship between Total_Firms and Male Executive Net Mean Salaries in Towns? 
```SQL
SELECT firms.libgeo,salary.SNHMHC14 as man_exec, firms.e14tst as Total_Firms
FROM datasets.french_employment_base_etablissement_par_tranche_effectif firms
JOIN datasets.french_employment_net_salary_per_town_categories salary
ON firms.libgeo = salary.libgeo
order by total_firms DESC
```

-- 7. What is the gender gap between Executive Female and Male Net Salary/hour in Firms of 500 employees?
E14TS500 : number of firms with more than 500 employees in the town

-- What is the relationship between Big500_Firms and Female Executive Salaries in Towns?
```SQL
SELECT firms.libgeo,salary.SNHMFC14 as FEM_exec, firms.E14TS500 as Big500_Firms
FROM datasets.french_employment_base_etablissement_par_tranche_effectif firms
JOIN datasets.french_employment_net_salary_per_town_categories salary
ON firms.libgeo = salary.libgeo
order by Big500_firms DESC
```

-- What is the relationship between Big500_Firms and Male Executive Salaries in Towns?
```SQL
SELECT firms.libgeo,salary.SNHMHC14 as MEN_exec, firms.E14TS500 as Big500_Firms
FROM datasets.french_employment_base_etablissement_par_tranche_effectif firms
JOIN datasets.french_employment_net_salary_per_town_categories salary
ON firms.libgeo = salary.libgeo
order by Big500_firms DESC
```

-- 8. What is the gender gap between Woman and Men Net Salary/Hr from 18-50 years?
NHMF2614 : mean net salary per hour for women between 26-50 years old
SNHMH2614 : mean net salary per hour for men between 26-50 years old

-- What is the relationship between Total_Firms and Female (18-50) Net Mean Salaries in Towns?
```SQL
SELECT firms.libgeo,salary.NHMF2614 as fem_1850, firms.e14tst as Total_Firms
FROM datasets.french_employment_base_etablissement_par_tranche_effectif firms
JOIN datasets.french_employment_net_salary_per_town_categories salary
ON firms.libgeo = salary.libgeo
order by total_firms DESC
```
 
-- What is the relationship between Total_Firms and Male (18-50) Net Mean Salaries in Towns?
```SQL
SELECT firms.libgeo,salary.SNHMH2614 as MEN_1850, firms.e14tst as Total_Firms
FROM datasets.french_employment_base_etablissement_par_tranche_effectif firms
JOIN datasets.french_employment_net_salary_per_town_categories salary
ON firms.libgeo = salary.libgeo
order by total_firms DESC
```

-- 9. Which age range by gender makes the most money?
```SQL
Males: 
SELECT libgeo, snhmh1814, SNHMH2614, SNHMH5014
from datasets.french_employment_net_salary_per_town_categories
where libgeo = 'Paris'
  
Female:
SELECT libgeo, snhmf1814, SNHMf2614, SNHMf5014 
from datasets.french_employment_net_salary_per_town_categories
where libgeo = 'Paris'

In a much smaller city(48 firms, Marzan)?
Male:
SELECT libgeo, snhmh1814, SNHMH2614, SNHMH5014
from datasets.french_employment_net_salary_per_town_categories
where libgeo = 'Marzan'

Female:
SELECT libgeo, snhmf1814, SNHMf2614, SNHMf5014 
from datasets.french_employment_net_salary_per_town_categories
where libgeo = 'Marzan'

Both: 
SELECT libgeo, snhmf1814, SNHMf2614, SNHMf5014, snhmh1814, SNHMH2614, SNHMH5014
from datasets.french_employment_net_salary_per_town_categories
where libgeo = 'Marzan'
```  

-- 10.What is the breakdown of small to large firms in the town with the most firms (Paris)?
```SQL
SELECT libgeo, e14ts1, e14ts6, e14ts10, e14ts20, e14ts50, e14ts100, e14ts200, e14ts500
FROM datasets.french_employment_base_etablissement_par_tranche_effectif
where libgeo = 'Paris'
```

-- In Marzan?
```SQL
SELECT libgeo, e14ts1, e14ts6, e14ts10, e14ts20, e14ts50, e14ts100, e14ts200, e14ts500
FROM datasets.french_employment_base_etablissement_par_tranche_effectif
where libgeo = 'Marzan'
```
