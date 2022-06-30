import sqlite3 as sql

connection = sql.connect("dabaseMovies.db")

pointer = connection.cursor()
pointer.execute("CREATE TABLE IF NOT EXISTS MOVIES( NAME TEXT, ACTOR TEXT, ACTRESS TEXT,DIRECTOR_NAME TEXT, YEAR INTEGER )")
pointer.execute("INSERT INTO MOVIES VALUES('Master','Vijay','Malavika Mohanan','Lokesh Kanagaraj',2021)")
pointer.execute("INSERT INTO MOVIES VALUES('Kgf','Yash','Srindhi Shetty','Prashanth Neel',2018)")
pointer.execute("INSERT INTO MOVIES VALUES('Asuran','Dhanush','Manju Warrier','Vetrimaaran',2019)")
pointer.execute("INSERT INTO MOVIES VALUES('Bashaa',RajiniKanth','Nagma','Suresh Krissna',1995)")
pointer.execute("INSERT INTO MOVIES VALUES('Comali','Jayam Ravi','Samyuktha Hegde',' Pradeep Ranganathan',2019)")

# Printing all the elements of the database 
print("************************Everything in the database************************")
allMovies = pointer.execute("SELECT * FROM MOVIES").fetchall()
for i in allMovies:
  title,actor,actress,director,releasedYear = i
  print("{t}\t\t{a}\t\t{ats}\t\t{d}\t\t{ry}".format(t=title,a=actor, ats=actress,d=director,ry=releasedYear))
  print("============================================================================================")

# In this query, we are printing only the details from the db where Dhanush is the lead actor
print("************************Actor Query************************")
actorQuery = pointer.execute("SELECT * FROM MOVIES WHERE ACTOR = 'Dhanush'").fetchall()
for i in actorQuery:
  title,actor,actress,director,releasedYear = i
  print("{t}\t\t{a}\t\t{ats}\t\t{d}\t\t{ry}".format(t=title,a=actor, ats=actress,d=director,ry=releasedYear))
  print("============================================================================================")
