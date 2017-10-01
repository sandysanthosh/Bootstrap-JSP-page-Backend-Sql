Welcome to the Bootstrap-JSP-page-Backend-Sql wiki!



`
<%@ page import="java.sql.*" %>
<%@ page import="java.io.*" %> 
<html>
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/css/bootstrap.min.css" integrity="sha384-/Y6pD6FV/Vv2HJnA6t+vslU6fwYXjCFtcEpHbNJ0lyAFsXTsjBbfaDjzALeQsN6M" crossorigin="anonymous">
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0-beta/js/bootstrap.min.js" integrity="sha384-h0AbiXch4ZDo7tp9hKZ4TsHbi047NrKGLO3SEJAg45jXxnGIfYzk4Si90RDIqNm1" crossorigin="anonymous"></script>
    </head>
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="css/bootstrap.min.css" rel="stylesheet">
<body>
	<form method="post">

		<table class="table table-striped table-inverse">
		<thead>
    <tr>
    <th>id</th>
	<th>Name</th>
	<th>Subject</th>
    </tr>
			</thead>
			 
			<%
			try
			{
		
		Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/sandy","root","sandy");
       PreparedStatement stmt1=con.prepareStatement("select * from school");
		ResultSet rs1=stmt1.executeQuery();
		while(rs1.next())
		{
			%>
			 <tbody>
		<tr class="table-active">
		
    <td><%=rs1.getInt("id") %></td>
    <td><%=rs1.getString("name") %></td>
    <td><%=rs1.getString("subject") %></td>
</tr>
			</tbody>
			<%
				}
			%>
			
		</table>
		<%
			rs1.close();
				stmt1.close();
				con.close();
			} catch (Exception e) {
				e.printStackTrace();
			}
		%>

	</form>
 <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="js/bootstrap.min.js"></script>
</body>
</html>`
