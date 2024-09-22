-- Create a table to store general data
CREATE TABLE general_data (
    id SERIAL PRIMARY KEY,
    data_type VARCHAR(255) NOT NULL,
    data_value TEXT NOT NULL,
    created_at TIMESTAMP WITHOUT TIME ZONE DEFAULT NOW()
);

-- Insert some sample data
INSERT INTO general_data (data_type, data_value) VALUES
    ('user_name', 'John Doe'),
    ('user_email', 'john.doe@example.com'),
    ('product_name', 'Laptop'),
    ('product_price', '1200'),
    ('order_id', '12345'),
    ('order_date', '2023-10-26');

-- Retrieve all data from the table
SELECT * FROM general_data;

-- Retrieve data by data type
SELECT * FROM general_data WHERE data_type = 'user_name';

-- Retrieve data by data value
SELECT * FROM general_data WHERE data_value LIKE '%Doe%';

-- Update a data value
UPDATE general_data SET data_value = 'Jane Doe' WHERE id = 1;

-- Delete a data entry
DELETE FROM general_data WHERE id = 2;

-- Aggregate data by data type
SELECT data_type, COUNT(*) AS count FROM general_data GROUP BY data_type;

-- Example: Calculate the average price of a product
SELECT AVG(CAST(data_value AS NUMERIC)) AS average_price
FROM general_data
WHERE data_type = 'product_price';

-- Example: Find the most recent order
SELECT data_value AS order_id, MAX(created_at) AS latest_order_date
FROM general_data
WHERE data_type = 'order_id';
