Run docker image
`docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Superstr*ng-p4ssword'  -p 1433:1433 --name mssql -d rizkyario/mssql-server-linux`

Initiate database
`cat init-profile-db.sql | docker exec -i mssql sqlcmd -S localhost -U sa -P Superstr*ng-p4ssword -t 30`

Set ADO.Net connection string. Make sure TrustServerCertificate=True
`Server={{docker-machine-ip-address}},1433;Initial Catalog=bikesharing-services-profilesName;Persist Security Info=False;User ID=sa;Password={{superstrong-password}};MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=True;Connection Timeout=30;`
