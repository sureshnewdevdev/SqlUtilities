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
