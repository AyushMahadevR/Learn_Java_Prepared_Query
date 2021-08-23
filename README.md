# How to execute SQL queries using Java

 - PreparedStatement interface for performing mysql queries.
 
 - PreparedStatement will be compiled first and parameters will be inserted and executed later 
hence fast performance.

 - PreparedStatement.executeUpdate() -> returns either no of rows affected or 0 for no return value operations.

 - PreparedStatement.executeQuery() -> returns one or more result sets.

```java
String empnum, phonenum;
Connection con;
PreparedStatement pstmt;
ResultSet rs;
…
pstmt = con.prepareStatement(
  "SELECT EMPNO, PHONENO FROM EMPLOYEE WHERE EMPNO=?"); 
                                  // Create a PreparedStatement object    
pstmt.setString(1,"000010");      // Assign value to input parameter      

rs = pstmt.executeQuery();        // Get the result table from the query  
while (rs.next()) {               // Position the cursor                  
 empnum = rs.getString(1);        // Retrieve the first column value
 phonenum = rs.getString(2);      // Retrieve the first column value
 System.out.println("Employee number = " + empnum +
   "Phone number = " + phonenum);
                                  // Print the column values
}
rs.close();                       // Close the ResultSet                  
pstmt.close();                    // Close the PreparedStatement                                                
```
