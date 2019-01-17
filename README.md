# JDBC_Assignment2
SQL2A
CREATE TABLE `sqlandjava`.`cars` (
  `car_id` INT(11) NOT NULL,
  `brand` VARCHAR(45) NOT NULL,
  `color` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`car_id`));
  INSERT INTO `sqlandjava`.`cars` (`car_id`, `brand`, `color`) VALUES ('1', 'Volvo', 'Black');
INSERT INTO `sqlandjava`.`cars` (`car_id`, `brand`, `color`) VALUES ('2', 'Saab', 'Blue');
INSERT INTO `sqlandjava`.`cars` (`car_id`, `brand`, `color`) VALUES ('3', 'Audi', 'Red');
INSERT INTO `sqlandjava`.`cars` (`car_id`, `brand`, `color`) VALUES ('4', 'Ford', 'Green');
CREATE USER user@localhost IDENTIFIED BY 'password'; 
GRANT SELECT ON sqlandjava.cars TO user@localhost;
package sqlandjava;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;

 import java.sql.Statement;

 public class Assignment2 {

	public static Connection getConnection() throws Exception {
		try {
			String url = "jdbc:mysql://localhost:3306/sqlandjava";
			String username = "user";
			String password = "password";
			
			Connection conn = DriverManager.getConnection(url,username,password);
			System.out.println("Connected to Database!");
			return conn;
		}catch(Exception e)
		{
			System.out.println(e);
		}
		return null;
	}
	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
        Connection conn = getConnection();
        Statement statment = conn.createStatement();
        ResultSet res = statment.executeQuery("select*from cars");
        while(res.next()) {
        	//System.out.println(res.getString("id"));
        	System.out.println(res.getString("car_id")+ ":" + res.getString("brand")+" "+ res.getString("color"));

        
        }
	}

}

1:Volvo Black
2:Saab Blue
3:Audi Red
4:Ford Green
