# SQL_Project
CREATE TABLE Patients (
    PatientID INT PRIMARY KEY,
    Name VARCHAR(100),
    Address VARCHAR(255),
    Phone VARCHAR(20),
    DateOfBirth DATE,
    Gender VARCHAR(10)
    -- Add more attributes as needed
);

CREATE TABLE Doctors (
    DoctorID INT PRIMARY KEY,
    Name VARCHAR(100),
    Specialization VARCHAR(100),
    Phone VARCHAR(20),
    Email VARCHAR(100)
    -- Add more attributes as needed
);

CREATE TABLE Appointments (
    AppointmentID INT PRIMARY KEY,
    PatientID INT,
    DoctorID INT,
    AppointmentDateTime DATETIME,
    Status VARCHAR(20), -- Scheduled, Completed, Cancelled, etc.
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID),
    FOREIGN KEY (DoctorID) REFERENCES Doctors(DoctorID)
    -- Add more attributes as needed
);

CREATE TABLE MedicalRecords (
    RecordID INT PRIMARY KEY,
    PatientID INT,
    DateOfVisit DATE,
    Diagnosis VARCHAR(255),
    Treatment VARCHAR(255),
    DoctorNotes TEXT,
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID)
    -- Add more attributes as needed
);

CREATE TABLE Billing (
    BillingID INT PRIMARY KEY,
    PatientID INT,
    Amount DECIMAL(10, 2),
    PaymentStatus VARCHAR(20), -- Paid, Unpaid, Partial
    DueDate DATE,
    FOREIGN KEY (PatientID) REFERENCES Patients(PatientID)
    -- Add more attributes as needed
);

CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
    -- Add more attributes as needed
);

CREATE TABLE Staff (
    StaffID INT PRIMARY KEY,
    Name VARCHAR(100),
    Role VARCHAR(100),
    DepartmentID INT,
    Phone VARCHAR(20),
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
    -- Add more attributes as needed
);

CREATE TABLE Wards (
    WardID INT PRIMARY KEY,
    WardName VARCHAR(100),
    Capacity INT,
    AvailableBeds INT
    -- Add more attributes as needed
);
