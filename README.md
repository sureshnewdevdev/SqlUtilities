# SqlUtilities 

 This a stored procedure for Finding Age 
SQL
CREATE PROCEDURE CheckDatesLessThan (
    @input1 VARCHAR(255),
    @input2 VARCHAR(255)
)
AS
BEGIN
    DECLARE @date1 DATE, @date2 DATE;

    -- Attempt to convert string inputs to DATE type
    SET @date1 = TRY_CONVERT(DATE, @input1);
    SET @date2 = TRY_CONVERT(DATE, @input2);

    -- Check if both conversions were successful
    IF (@date1 IS NOT NULL AND @date2 IS NOT NULL)
    BEGIN
        IF (@date1 < @date2)
        BEGIN
            SELECT 1 AS IsLessThan; -- Indicates input1 is less than input2
        END
        ELSE
        BEGIN
            SELECT 0 AS IsLessThan; -- Indicates input1 is not less than input2
        END
    END
    ELSE
    BEGIN
        RAISERROR('Invalid date format in input strings.', 16, 1);
    END
END
