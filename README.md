# DB_Project01, Steps


# Step 01, CRUD operations using PGADMIN
CREATE TABLE team(
	team_id INT PRIMARY KEY,
	team_name VARCHAR(20),
	teamleader_id INT,
	manager_id INT,
	FOREIGN KEY(manager_id) REFERENCES developer(dev_id) ON DELETE SET NULL
);

CREATE TABLE developer(
	dev_id INT PRIMARY KEY,
	first_name VARCHAR(20),
	last_name VARCHAR(20),
	age INT,
	gender VARCHAR(15),
	salary INT,
	teamleader_id INT,
	team_id INT
);

CREATE TABLE project(
	project_id INT PRIMARY KEY,
	project_name VARCHAR(20),
	team_id INT,
	FOREIGN KEY(team_id) REFERENCES team(team_id) ON DELETE SET NULL
);

CREATE TABLE assigned_to(
	dev_id INT,
	project_id INT,
	budget INT,
	PRIMARY KEY(dev_id, project_id),
	FOREIGN KEY(dev_id) REFERENCES developer(dev_id) ON DELETE CASCADE,
	FOREIGN KEY(project_id) REFERENCES project(project_id) ON DELETE CASCADE
);

CREATE TABLE investor(
	team_id INT,
	inverstor_name VARCHAR(20),
	project_tech VARCHAR(20),
	PRIMARY KEY(team_id, inverstor_name),
	FOREIGN KEY(team_id) REFERENCES team(team_id) ON DELETE CASCADE
);
