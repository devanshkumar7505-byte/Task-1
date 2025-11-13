# Task-1
Data cleaning task given on first day of internship with elevate labs.

Project Overview

  ​This project involved cleaning and normalizing a raw Amazon Product dataset. The original dataset contained encoding errors, merged columns, misplaced data values, and inconsistent       formatting. The goal was to create a clean, structured dataset ready for analysis.
​🛠 Tools Used

​Software: Microsoft Excel
​Key Techniques: Power Query, Flash Fill, Text-to-Columns, Conditional Logic Formulas, Duplicate Removal.

​🧹 Data Cleaning Process

​1. Price Standardization (discounted_price & actual_price)
​Issue: Currency symbols were corrupted (appearing as â,¹ instead of ₹) and numbers were stored as text.
​Action:
​Removed garbage characters using Find & Replace.
​Converted columns to numeric format using Text to Columns.
​Rounded decimal values to whole numbers using the ROUND() function.
​Formula Used: =ROUND(C2, 0)
​2. User Name Extraction & Normalization
​Issue: User names were delimited by pipes (|) or commas and spread across multiple columns (H through L).
​Action:
​Extracted the last distinct name using TEXTAFTER or Flash Fill.
​Merged multiple columns into a single vertical list using the TOCOL function (stacking columns H-L).
​Formula Used: =SORT(TOCOL(H2:L100, 1))
​3. Rating Count Alignment
​Issue: Data shift error. Some rating_count values were merged into the previous column or contained text/dates.
​Action:
​Used conditional logic to check for empty cells and retrieve the displaced data from the adjacent column.
​Cleaned formatting (removed commas) to ensure numeric consistency.
​Formula Used: =IF(G2="", RIGHT(F2, LEN(F2)-FIND(" ", F2)), G2)
​4. Data Integrity & Quality Control
​Handling Nulls: Identified blank values in pricing columns and removed invalid rows.
​Removing Junk Data: Filtered and removed rows containing generic placeholders (e.g., "Placeholder", "Amazon Customer") or invalid characters (e.g., single letters, symbols).
​Deduplication: Identified and removed duplicate records to ensure unique observations where necessary.
​5. Finalization
​Formula Removal: Converted all calculated columns (Cleaned Prices, Merged Names) into static data using Paste Values to prevent reference errors when deleting helper columns.

​📊 Final Dataset Structure
​The cleaned dataset now contains the following standardized columns:
​User_Name: Cleaned, single string names.
​Rating: Numeric value (0-5).
​Rating_Count: Integer value representing total reviews.
​Discounted_Price: Integer value (Currency cleaned).
