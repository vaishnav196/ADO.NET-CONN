# ADO.NET-CONN
1)Connection String Setup (App.config)

<configuration>
  <connectionStrings>
    <add name="DbConnection"
         connectionString="Server=YOUR_SERVER;
                           Database=YOUR_DB;
                           Trusted_Connection=True;"
         providerName="System.Data.SqlClient"/>
  </connectionStrings>
</configuration>


2)Creating SQL Connection (DbConnectionFactory.cs)


using System.Configuration;
using System.Data.SqlClient;
-------------------

    public static class DbConnectionFactory
    {
        public static SqlConnection GetConnection()
        {
            string connStr =
                ConfigurationManager.ConnectionStrings["DbConnection"].ConnectionString;

            return new SqlConnection(connStr);
        }
    }


-----------------

public List<Employee> GetAllEmployees()
{
    var employees = new List<Employee>();

    using (SqlConnection conn = DbConnectionFactory.GetConnection())
    {
        SqlCommand cmd = new SqlCommand("SELECT Id, Name, Salary FROM Employee", conn);
        conn.Open();

        SqlDataReader reader = cmd.ExecuteReader();
        while (reader.Read())
        {
            employees.Add(new Employee
            {
                Id = reader.GetInt32(0),
                Name = reader.GetString(1),
                Salary = reader.GetDecimal(2)
            });
        }
    }
    return employees;
}

------------------------------

using (SqlConnection conn = new SqlConnection(connectionString))
{
    conn.Open();
}


------------------


