### Connection to Azure SQL Database using pymssql
SERVER = os.environ.get("SETTLEMENT_SERVER")
DATABASE = os.environ.get("SETTLEMENT_DATABASE")
USER = os.environ.get("SETTLEMENT_USER")
PASSWORD = os.environ.get("SETTLEMENT_PASSWORD")
PORT = os.environ.get("SETTLEMENT_PORT")

DATABASE_URL = f"mssql+pymssql://{USER}:{PASSWORD}@{SERVER}:{PORT}/{DATABASE}"


### connection to Azure SQL Database using ODBC
import urllib
params = urllib.parse.quote_plus(
     f'Driver={{ODBC Driver 18 for SQL Server}};Server=tcp:{SERVER},{PORT};Database={DATABASE};Uid={USER};Pwd={PASSWORD};Encrypt=yes;TrustServerCertificate=no;Connection Timeout=30;'
)

DATABASE_URL = f'mssql+pyodbc:///?odbc_connect={params}'