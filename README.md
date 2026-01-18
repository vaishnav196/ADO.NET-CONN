# ADO.NET-CONN
Connection String Setup (App.config)
<configuration>
  <connectionStrings>
    <add name="DbConnection"
         connectionString="Server=YOUR_SERVER;
                           Database=YOUR_DB;
                           Trusted_Connection=True;"
         providerName="System.Data.SqlClient"/>
  </connectionStrings>
</configuration>
