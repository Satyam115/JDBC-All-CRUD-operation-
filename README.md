# JDBC-All-CRUD-operation-
This is my JDBC crud operation code with placeholder 

// Insert a data in database
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
public class Demo1 {
	public static void main(String[] args) {
		String query="insert into jdbc.employee values(3,'raja','software developer',400000)";
		String url="jdbc:mysql://localhost:3306?user=root&password=root";
try {
	Class.forName("com.mysql.cj.jdbc.Driver");
	System.out.println("step 1 is done");
	
	Connection con =DriverManager.getConnection(url);
	System.out.println("step 2 is done");
	
	Statement stmt=con.createStatement();
	System.out.println("step 3 is done");
	
	stmt.executeUpdate(query);
	System.out.println("step 4 is done");
}catch(Exception e) {
e.printStackTrace();

}
}
}

// Update a data in database
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class UpdateData {
public static void main(String[] args) {
	
	String url="jdbc:mysql://localhost:3306?user=root&password=root";
	String query="update satyam.info set salery=9000,name='ram' where id=2";
	try {
		Class.forName("com.mysql.cj.jdbc.Driver");
		
		Connection con=DriverManager.getConnection(url);
		
		Statement stmt=con.createStatement();
		
	Int  result=stmt.executeUpdate(query);
		
	if (result==1) {
		System.out.println("data inserted successfully");
	} else {
		System.out.println("data  Not inserted successfully   !!!!!!!!!!!");
	}
	}catch(Exception e) {
		e.printStackTrace();
	}
	}
                    }


//  Delete a data in database
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class DeleteData {
	public static void main(String[] args) {
		
		String url="jdbc:mysql://localhost:3306?user=root&password=root";
		String query="delete from satyam.info where id=1";
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			
			Connection con=DriverManager.getConnection(url);
			
			Statement stmt=con.createStatement();
			
		int	result=stmt.executeUpdate(query);
			
		if (result==1) {
			System.out.println("data deleted successfully");
		} else {
			System.out.println("data  Not deleted successfully   !!!!!!!!!!!");
		}
		}catch(Exception e) {
				e.printStackTrace();
			}
		                 }
                                                    }
//  Fatch all data in database
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class FatchAllRecords {
	public static void main(String[] args) {

		String url = "jdbc:mysql://localhost:3306?user=root&password=root";
		String query = "select* from satyam.info ";
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");

			Connection con = DriverManager.getConnection(url);

			Statement stmt = con.createStatement();

			ResultSet rs = stmt.executeQuery(query);
			while (rs.next()) {
				int id = rs.getInt(1);
				System.out.print("Id =" + id + "\t");
				String name = rs.getString(2);
				System.out.print("Name =" + name + "\t");
				double salery = rs.getDouble(3);
				System.out.print("Salery =" + salery + "\t");
				System.out.println("");
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
                                   }    }
//  INSERT data in database with the help of placeholder
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Scanner;

public class JdbcWithPlaceHolder {

	public static void main(String[] args) {
Scanner sc=new Scanner(System.in);
System.out.println("Enter the id here");
int id=sc.nextInt();
System.out.println("Enter the name here");
String name=sc.next();
System.out.println("Enter the salery here");
double salery=sc.nextDouble();

String url="jdbc:mysql://localhost:3306?user=root&password=root";
String query="insert into satyam.info values(?,?,?)";
try {
	Class.forName("com.mysql.cj.jdbc.Driver");
	System.out.println("step 1 is done");
	
	Connection con =DriverManager.getConnection(url);
	System.out.println("step 2 is done");

	PreparedStatement pstmt=con.prepareStatement(query);
	System.out.println("step 3 is done");
	
	pstmt.setInt(1, id);
	pstmt.setString(2, name);
	pstmt.setDouble(3, salery);
	System.out.println("step 4 is done");
	pstmt.executeUpdate();
	System.out.println("data inserted successfully  !!!!!!!!!!!!!!!");

}catch(Exception e) {
		e.printStackTrace();	
	}
	}
                  }
//  Update  data in database with the help of placeholder
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Scanner;

public class UpdateRecordsWithPlaceholder {
public static void main(String[] args) {
	String query="update satyam.info set name=?,salery=? where id=?";
	String url="jdbc:mysql://localhost:3306?user=root&password=root";
	
	Scanner sc=new Scanner(System.in);
	System.out.println("Enter the id here");
    int id=sc.nextInt();
    
	System.out.println("Enter the name here");
	String name=sc.next();
	
	System.out.println("Enter the salery here");
    double salery=sc.nextDouble();
    
    
    try {
    	Class.forName("com.mysql.cj.jdbc.Driver");
    	
    	Connection con =DriverManager.getConnection(url);
    	
    	PreparedStatement pstmt=con.prepareStatement(query);
    	
    	pstmt.setInt(3, id);
    	pstmt.setString(1, name);
    	pstmt.setDouble(2, salery);
    	
    	int result=pstmt.executeUpdate();
if(result==1) {
	System.out.println("data updated successfully");
}else {
	System.out.println("data Not updated successfully");

}
    	
    }catch(Exception e) {
    	e.printStackTrace();
    }
	
}
}

//  Delete  data in database with the help of placeholder
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.util.Scanner;

public class DeleteDataWithPlaceholder {
	public static void main(String[] args) {
		String query="delete from satyam.info where id=?";
		String url="jdbc:mysql://localhost:3306?user=root&password=root";
		
		Scanner sc=new Scanner(System.in);
		System.out.println("Enter the id here");
	    int id=sc.nextInt();
	    
	    try {
	    	Class.forName("com.mysql.cj.jdbc.Driver");
	    	
	    	Connection con =DriverManager.getConnection(url);
	    	
	    	PreparedStatement pstmt=con.prepareStatement(query);
	    	
	    	pstmt.setInt(1, id);
	    	
	    	int result=pstmt.executeUpdate();
	if(result==1) {
		System.out.println("data Deleted successfully");
	}else {
		System.out.println("data Not Deleted successfully");

	}
	    	
	    }catch(Exception e) {
	    	e.printStackTrace();
	    }
	}
}


//  Fatch  data in database with the help of placeholder
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.util.Scanner;

public class FatchTheRecordWithPlaceHolder {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter the id here");
		int id = sc.nextInt();
		
		String url = "jdbc:mysql://localhost:3306?user=root&password=root";
		String query = "select* from satyam.info where id=?";
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");

			Connection con = DriverManager.getConnection(url);

			PreparedStatement pstmt = con.prepareStatement(query);

			pstmt.setInt(1, id);
			ResultSet rs= pstmt.executeQuery();

			if(rs.next()) {
				int sid=rs.getInt(1);
				String name=rs.getString(2);
			System.out.println("id :-"+sid+", name :-"+name);
			}else {
				System.out.println("sorry data id not present");
		}	
		} catch (Exception e) {
			e.printStackTrace();
		}
                                                main(args);
	                }
                                 }

// Servlet dependency

<!-- https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api -->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>4.0.1</version>
    <scope>provided</scope>
</dependency>

//  Jsp dependency
<!-- https://mvnrepository.com/artifact/javax.servlet.jsp/javax.servlet.jsp-api -->
<dependency>
    <groupId>javax.servlet.jsp</groupId>
    <artifactId>javax.servlet.jsp-api</artifactId>
    <version>2.3.3</version>
    <scope>provided</scope>
</dependency>



//  Mysql dependency
<!-- https://mvnrepository.com/artifact/com.mysql/mysql-connector-j -->
<dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <version>8.1.0</version>
</dependency>

