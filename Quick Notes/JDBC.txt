package com.demo.Main;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
import java.sql.Statement;

public class TestMain {

	public static void main(String[] args) throws ClassNotFoundException {
		final String user = "root";
		final String pass = "Rushikesh@5046";
		final String sqlcon = "jdbc:mysql://localhost:3306/rushi";
		Connection con = null;
		PreparedStatement pst = null;
		Statement statement = null;
		ResultSet rs = null;

		Class.forName("com.mysql.cj.jdbc.Driver");
		try {

			int userId = 1;
			String password = "Rushi";
			String Email_id = "R@gmail.com";
			con = DriverManager.getConnection(sqlcon, user, pass);

			/************************** Insert for *******************/
			pst = con.prepareStatement("INSERT INTO IET values (?,?,?)");

			pst.setInt(1, userId);

			pst.setString(2, password);

			pst.setString(3, Email_id);
			
			

			// ******************* Update for*******************/
			pst = con.prepareStatement("update IET set password = ? where userId = ?");

			pst.setString(1, password);
			pst.setInt(2, userId);

			
			
			// **************************Delte for*******************/
			pst = con.prepareStatement("DELETE FROM IET  WHERE userId='" + userId + "' ");
			
			

			// **************************Select Query for*******************/
			statement = con.createStatement();

			rs = statement.executeQuery("SELECT * FROM iet");

			while (rs.next()) {
				int user_Id = rs.getInt("userId");
				String Password = rs.getString("password");
				String Email = rs.getString("Email_id");
				System.out.println("User ID: " + user_Id + ", Password: " + Password + " , Email: " + Email);
			}
			
			

			// **************************Validation*******************/
			int rowsAffected = pst.executeUpdate();

			// Checking if the update was successful
			if (rowsAffected > 0) {
				System.out.println("successfully for user: " + userId);
			} else {
				System.out.println("No user found with the username: " + userId);
			}

			System.out.println("Successfully");

		} catch (SQLException e) {

			e.printStackTrace();
		}

	}
}
