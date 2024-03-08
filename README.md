# SqlUtilities 

 This a stored procedure for Finding Age 
SQL

Explain
CREATE PROCEDURE GetAge 
(
  @dateOfBirth DATE
)
AS
BEGIN
  DECLARE @age INT;

  SET @age = FLOOR(DATEDIFF(YEAR, @dateOfBirth, GETDATE()) - 
                  CASE WHEN MONTH(GETDATE()) < MONTH(@dateOfBirth) OR 
                         (MONTH(GETDATE()) = MONTH(@dateOfBirth) AND DAY(GETDATE()) < DAY(@dateOfBirth))
                   THEN 1
                   ELSE 0
                  END);

  SELECT @age AS Age;
END;

go


Stored procedure to find the given date is greater than current date or not.

CREATE PROCEDURE IsDateOnOrAfterToday (@dateToCheck DATE)
AS
BEGIN
  DECLARE @isDateOnOrAfterToday BIT;

  SET @isDateOnOrAfterToday = CAST((@dateToCheck >= GETDATE()) AS BIT);

  SELECT @isDateOnOrAfterToday AS IsDateOnOrAfterToday;
END;




