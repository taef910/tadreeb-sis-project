CREATE TABLE IF NOT EXISTS Internship (
    internshipID INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(150) NOT NULL,
    company VARCHAR(150) NOT NULL,
    description TEXT,
    requirement TEXT,
    location VARCHAR(150),
    duration VARCHAR(100),
    semester VARCHAR(50),
    deadline DATE,
    isVerified BOOLEAN DEFAULT FALSE
);

DELIMITER //
CREATE PROCEDURE addInternship(
    IN p_title VARCHAR(150),
    IN p_company VARCHAR(150),
    IN p_description TEXT,
    IN p_requirement TEXT,
    IN p_location VARCHAR(150),
    IN p_duration VARCHAR(100),
    IN p_semester VARCHAR(50),
    IN p_deadline DATE
)
BEGIN
    INSERT INTO Internship (title, company, description, requirement, location, duration, semester, deadline, isVerified)
    VALUES (p_title, p_company, p_description, p_requirement, p_location, p_duration, p_semester, p_deadline, FALSE);
END //
DELIMITER ;

DELIMITER //
CREATE PROCEDURE updateDetails(
    IN p_internshipID INT,
    IN p_title VARCHAR(150),
    IN p_company VARCHAR(150),
    IN p_description TEXT,
    IN p_requirement TEXT,
    IN p_location VARCHAR(150),
    IN p_duration VARCHAR(100),
    IN p_semester VARCHAR(50),
    IN p_deadline DATE
)
BEGIN
    UPDATE Internship
    SET
        title = p_title,
        company = p_company,
        description = p_description,
        requirement = p_requirement,
        location = p_location,
        duration = p_duration,
        semester = p_semester,
        deadline = p_deadline
    WHERE internshipID = p_internshipID;
END //
DELIMITER ;

DELIMITER //
CREATE PROCEDURE verifyInternship(
    IN p_internshipID INT
)
BEGIN
    UPDATE Internship
    SET isVerified = TRUE
    WHERE internshipID = p_internshipID;
END //
DELIMITER ;

CREATE TABLE IF NOT EXISTS Bookmark (
    bookmarkID INT AUTO_INCREMENT PRIMARY KEY,
    studentID INT NOT NULL,
    internshipID INT NOT NULL,
    dateBookmarked DATE NOT NULL,
    UNIQUE(studentID, internshipID),
    FOREIGN KEY (internshipID) REFERENCES Internship(internshipID)
);

DELIMITER //
CREATE PROCEDURE addBookmark(
    IN p_studentID INT,
    IN p_internshipID INT,
    IN p_date DATE
)
BEGIN
    INSERT IGNORE INTO Bookmark (studentID, internshipID, dateBookmarked)
    VALUES (p_studentID, p_internshipID, p_date);
END //
DELIMITER ;

DELIMITER //
CREATE PROCEDURE removeBookmark(
    IN p_studentID INT,
    IN p_internshipID INT
)
BEGIN
    DELETE FROM Bookmark
    WHERE studentID = p_studentID AND internshipID = p_internshipID;
END //
DELIMITER ;
