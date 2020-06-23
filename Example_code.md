#MYSQL Example code
/* To view the table*/

SELECT * FROM MY_FAVORITE_FILMS;

/*Creating a database */

CREATE DATABASE daniel_db;
USE daniel_db;
/*using the database I just created */


/*Creating a table */

CREATE TABLE MY_FAVORITE_FILMS(
    film_name VARCHAR(15),
    film_type VARCHAR(15),
    date_of_release DATE,
    director VARCHAR(15),
    writer VARCHAR(15),
    star DECIMAL(2,1),
    film_language CHAR(3),
    official_website VARCHAR(50),
    plot_summary VARCHAR(100)
);

/*Adding another collum to the table*/

ALTER TABLE my_favorite_films
ADD release_date DATETIME;

ALTER TABLE my_favorite_films
ADD film_id INT IDENTITY(1,1) PRIMARY KEY;

/*dropping the table */

DROP TABLE MY_FAVORITE_FILMS;

INSERT INTO MY_FAVORITE_FILMS
(
    film_name, film_type, date_of_release, director, writer, star, film_language, official_website, plot_summary, release_date
)
VALUES 
(
    'Junglebook', 'Entertainment', '1994/09/17', 'Daniel Teegan', 'Daniel Teegan', 4.5, 'ENG', 'www.junglebook.com', 'This film is very good, very entertaining. This film is very good, very entertaining', '2002/07/19'
);

/*Shows the table*/

SP_HELP MY_FAVORITE_FILMS

CREATE TABLE director(
    director_id INT IDENTITY(1,1),
    director_name VARCHAR(50),
    city VARCHAR(20) DEFAULT 'London',
    film_id INT,
    PRIMARY KEY(director_id),
    FOREIGN KEY(film_id) REFERENCES my_favorite_films(film_id)
);

DROP TABLE director;

SELECT * FROM MY_FAVORITE_FILMS;
SELECT * FROM DIRECTOR;



INSERT INTO DIRECTOR
(director_name, film_id)
VALUES
('John', 1);

INSERT INTO DIRECTOR
(director_name, film_id)
VALUES
('John', 2);