CREATE TABLE restaurant (
  id INTEGER NOT NULL PRIMARY KEY, 
  name VARCHAR(20), 
  description VARCHAR(100) NOT NULL, 
  rating DECIMAL NOT NULL, 
  telephone CHAR(10) NOT NULL, 
  hours VARCHAR(100) NOT NULL
);
CREATE TABLE address (
  id INTEGER NOT NULL PRIMARY KEY REFERENCES restaurant(id) UNIQUE, 
  street_number VARCHAR(10) NOT NULL, 
  street_name VARCHAR(20) NOT NULL, 
  city VARCHAR(20) NOT NULL, 
  state VARCHAR(15) NOT NULL, 
  google_map_link VARCHAR(50) NOT NULL
);
SELECT 
  constraint_name, 
  table_name, 
  column_name 
FROM 
  information_schema.key_column_usage 
WHERE 
  table_name = 'restaurant';
SELECT 
  constraint_name, 
  table_name, 
  column_name 
FROM 
  information_schema.key_column_usage 
WHERE 
  table_name = 'address';
CREATE TABLE category (
  id CHAR(2) PRIMARY KEY, 
  name VARCHAR(20) NOT NULL, 
  description VARCHAR(200) UNIQUE
);
SELECT 
  constraint_name, 
  table_name, 
  column_name 
FROM 
  information_schema.key_column_usage 
WHERE 
  table_name = 'restaurant';
CREATE TABLE dish (
  id INTEGER PRIMARY KEY, 
  name VARCHAR(50) NOT NULL, 
  description VARCHAR(200), 
  hot_and_spicy BOOLEAN
);
SELECT 
  constraint_name, 
  table_name, 
  column_name 
FROM 
  information_schema.key_column_usage 
WHERE 
  table_name = 'dish';
CREATE TABLE review (
  id INTEGER NOT NULL PRIMARY KEY, 
  rating DECIMAL NOT NULL, 
  description VARCHAR(100), 
  date DATE, 
  restaurant_id INTEGER REFERENCES restaurant(id)
);
SELECT 
  constraint_name, 
  table_name, 
  column_name 
FROM 
  information_schema.key_column_usage 
WHERE 
  table_name = 'review';
CREATE TABLE categories_dishes (
  category_id CHAR(2) REFERENCES category(id), 
  dish_id INTEGER REFERENCES dish(id), 
  price MONEY, 
  PRIMARY KEY (category_id, dish_id)
);
SELECT 
  constraint_name, 
  table_name, 
  column_name 
FROM 
  information_schema.key_column_usage 
WHERE 
  table_name = 'categories_dishes';
INSERT INTO restaurant 
VALUES 
  (
    1, 'Bytes of China', 'Delectable Chinese Cuisine', 
    3.9, '6175551212', 'Mon - Fri 9:00 am to 9:00 pm, Weekends 10:00 am to 11:00 pm'
  );
INSERT INTO address 
VALUES 
  (
    1, '2020', 'Busy Street', 'Chinatown', 
    'MA', 'http://bit.ly/BytesOfChina'
  );
INSERT INTO review 
VALUES 
  (
    1, 5.0, 'Would love to host another birthday party at Bytes of China!', 
    '05-22-2020', 1
  );
INSERT INTO review 
VALUES 
  (
    2, 4.5, 'Other than a small mix-up, I would give it a 5.0!', 
    '04-01-2020', 1
  );
INSERT INTO review 
VALUES 
  (
    3, 3.9, 'A reasonable place to eat for lunch, if you are in a rush!', 
    '03-15-2020', 1
  );
INSERT INTO category 
VALUES 
  ('C', 'Chicken', null);
INSERT INTO category 
VALUES 
  (
    'LS', 'Luncheon Specials', 'Served with Hot and Sour Soup or Egg Drop Soup and Fried or Steamed Rice  between 11:00 am and 3:00 pm from Monday to Friday.'
  );
INSERT INTO category 
VALUES 
  ('HS', 'House Specials', null);
INSERT INTO dish 
VALUES 
  (
    1, 'Chicken with Broccoli', 'Diced chicken stir-fried with succulent broccoli florets', 
    false
  );
INSERT INTO dish 
VALUES 
  (
    2, 'Sweet and Sour Chicken', 'Marinated chicken with tangy sweet and sour sauce together with pineapples and green peppers', 
    false
  );
INSERT INTO dish 
VALUES 
  (
    3, 'Chicken Wings', 'Finger-licking mouth-watering entree to spice up any lunch or dinner', 
    true
  );
INSERT INTO dish 
VALUES 
  (
    4, 'Beef with Garlic Sauce', 'Sliced beef steak marinated in garlic sauce for that tangy flavor', 
    true
  );
INSERT INTO dish 
VALUES 
  (
    5, 'Fresh Mushroom with Snow Peapods and Baby Corns', 
    'Colorful entree perfect for vegetarians and mushroom lovers', 
    false
  );
INSERT INTO dish 
VALUES 
  (
    6, 'Sesame Chicken', 'Crispy chunks of chicken flavored with savory sesame sauce', 
    false
  );
INSERT INTO dish 
VALUES 
  (
    7, 'Special Minced Chicken', 'Marinated chicken breast sauteed with colorful vegetables topped with pine nuts and shredded lettuce.', 
    false
  );
INSERT INTO dish 
VALUES 
  (
    8, 'Hunan Special Half & Half', 'Shredded beef in Peking sauce and shredded chicken in garlic sauce', 
    true
  );
INSERT INTO categories_dishes 
VALUES 
  ('C', 1, 6.95);
INSERT INTO categories_dishes 
VALUES 
  ('C', 3, 6.95);
INSERT INTO categories_dishes 
VALUES 
  ('LS', 1, 8.95);
INSERT INTO categories_dishes 
VALUES 
  ('LS', 4, 8.95);
INSERT INTO categories_dishes 
VALUES 
  ('LS', 5, 8.95);
INSERT INTO categories_dishes 
VALUES 
  ('HS', 6, 15.95);
INSERT INTO categories_dishes 
VALUES 
  ('HS', 7, 16.95);
INSERT INTO categories_dishes 
VALUES 
  ('HS', 8, 17.95);
SELECT 
  restaurant.name, 
  address.street_number, 
  restaurant.telephone 
FROM 
  restaurant, 
  address 
WHERE 
  restaurant.name = 'Bytes of China';
SELECT 
  MAX(review.rating) AS best_rating 
FROM 
  review;
SELECT 
  dish.name AS Dish_Name, 
  categories_dishes.price AS Price, 
  category.id AS Category 
FROM 
  dish, 
  categories_dishes, 
  category 
WHERE 
  category.id = categories_dishes.category_id 
  AND categories_dishes.dish_id = dish.id 
ORDER BY 
  dish.name;
SELECT 
  category.id AS category, 
  dish.name AS dish_name, 
  categories_dishes.price AS price 
FROM 
  category, 
  dish, 
  categories_dishes 
WHERE 
  category.id = categories_dishes.category_id 
  AND categories_dishes.dish_id = dish.id 
ORDER BY 
  category.id;
SELECT 
  dish.name AS spicy_dish_name, 
  category.id AS category, 
  categories_dishes.price AS price 
FROM 
  dish, 
  category, 
  categories_dishes 
WHERE 
  dish.hot_and_spicy = 'TRUE' 
  AND category.id = categories_dishes.category_id 
  AND categories_dishes.dish_id = dish.id;
SELECT 
  categories_dishes.category_id AS dish_id, 
  COUNT(categories_dishes.category_id) AS dish_count 
FROM 
  categories_dishes 
GROUP BY 
  categories_dishes.category_id 
HAVING 
  COUNT(categories_dishes.category_id) > 1;
SELECT 
  dish.name AS dish_name, 
  COUNT(categories_dishes.category_id) AS dish_count 
FROM 
  dish, 
  categories_dishes 
GROUP BY 
  dish.name 
HAVING 
  COUNT(categories_dishes.category_id) > 1;
SELECT 
  review.rating, 
  review.description 
FROM 
  review 
WHERE 
  review.rating = (
    SELECT 
      MAX(rating) 
    FROM 
      review
  );
