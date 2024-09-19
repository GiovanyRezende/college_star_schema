# College Star Schema
*This is a challenge of Data Engineering NTT DATA Bootcamp in [DIO](https://web.dio.me/).* It consists in creating a simple Star Schema with a school or academic context.

## SQL Creation
```
CREATE TABLE IF NOT EXISTS dim_professor(
    id INT PRIMARY KEY,
    register INT NOT NULL,
    name VARCHAR(255) NOT NULL,
    department VARCHAR(200) NOT NULL,
    discipline VARCHAR(150) NOT NULL,
    CONSTRAINT uq_dim_professor UNIQUE (register)
);

CREATE TABLE IF NOT EXISTS dim_student(
    id INT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    course VARCHAR(150) NOT NULL
);

CREATE TABLE IF NOT EXISTS dim_date(
    id INT PRIMARY KEY,
    year YEAR NOT NULL,
    month INT NOT NULL,
    day INT NOT NULL
);

CREATE TABLE IF NOT EXISTS ft_project(
    id INT PRIMARY KEY,
    name VARCHAR(200),
    description VARCHAR(255),
    score DECIMAL(4,2) CHECK (score <= 10) NOT NULL,
    id_professor INT NOT NULL,
    id_student INT NOT NULL,
    id_date INT NOT NULL,
    CONSTRAINT fk_project_professor FOREIGN KEY (id_professor)
    REFERENCES dim_professor (id),
    CONSTRAINT fk_project_student FOREIGN KEY (id_student)
    REFERENCES dim_student (id),
    CONSTRAINT fk_project_date FOREIGN KEY (id_date)
    REFERENCES dim_date (id)
);
```

## The Star Schema
![image](https://github.com/user-attachments/assets/5f153b41-b6f9-40f9-839d-9323b06325b1)

