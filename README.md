Question 1: Total Number of Invoices
SELECT COUNT(*) AS total_invoices
FROM invoices;
Question 2: Total Amount of All Invoices
SELECT SUM(invoice_total) AS total_invoice_amount
FROM invoices;

Question 3: Average Invoice Total
SELECT AVG(invoice_total) AS average_invoice_total
FROM invoices;

Question 4: Highest and Lowest Invoice Totals
SELECT MAX(invoice_total) AS highest_invoice_total,
       MIN(invoice_total) AS lowest_invoice_total
FROM invoices;

Question 5: Total Amount Paid by Each Vendor
SELECT vendor_id, SUM(payment_total) AS total_amount_paid
FROM invoices
GROUP BY vendor_id
ORDER BY total_amount_paid DESC;

Question 6: Total Number of Invoices and Total Invoice Amount by Vendor
SELECT vendor_id, 
       COUNT(*) AS invoice_count, 
       SUM(invoice_total) AS total_invoice_amount
FROM invoices
GROUP BY vendor_id
ORDER BY total_invoice_amount DESC;
Question 7: Total Line Item Amount for Each General Ledger Account
SELECT account_number, 
       SUM(line_item_amount) AS total_line_item_amount
FROM invoice_line_items
GROUP BY account_number
ORDER BY total_line_item_amount DESC;

Question 8: Total Invoice Amount for Each Vendor with ROLLUP

SELECT vendor_id, 
       SUM(invoice_total) AS total_invoice_amount
FROM invoices
GROUP BY vendor_id WITH ROLLUP;
