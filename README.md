# sql---6
הכנה למבחן 1
-- טבלת קטגוריות
CREATE TABLE category (
    id_category SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

-- טבלת מוצרים
CREATE TABLE products (
    id_product SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    price NUMERIC(10, 2) NOT NULL,
    id_category INT,
    FOREIGN KEY (id_category) REFERENCES category(id_category)
);

-- טבלת ערכים תזונתיים
CREATE TABLE nutritions (
    id_nutrition SERIAL PRIMARY KEY,
    id_product INT NOT NULL,
    name VARCHAR(100) NOT NULL,
    calories NUMERIC(10, 2),
    fats NUMERIC(10, 2),
    sugar NUMERIC(10, 2),
    FOREIGN KEY (id_product) REFERENCES products(id_product)
);

-- טבלת הזמנות
CREATE TABLE orders (
    id_order SERIAL PRIMARY KEY,
    time_date TIMESTAMP NOT NULL,
    address VARCHAR(200) NOT NULL,
    name_customer VARCHAR(100) NOT NULL,
    ph_customer VARCHAR(15) NOT NULL,
    price_total NUMERIC(10, 2) NOT NULL
);

-- טבלת מוצרים בהזמנות
CREATE TABLE orders_products (
    id_order INT NOT NULL,
    id_product INT NOT NULL,
    amount INT NOT NULL,
    PRIMARY KEY (id_order, id_product),
    FOREIGN KEY (id_order) REFERENCES orders(id_order),
    FOREIGN KEY (id_product) REFERENCES products(id_product)
);
