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

namespace Data
{
    public static class DbConnectionFactory
    {
        public static SqlConnection GetConnection()
        {
            string connStr =
                ConfigurationManager.ConnectionStrings["DbConnection"].ConnectionString;

            return new SqlConnection(connStr);
        }
    }
}

