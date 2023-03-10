# MongoDB_Practical
* By simply giving the command ‘use dbname’ we can create the database in Mongodb. 

* After that we need to make a collection which is analogous to tables in SQL. 

* For the sake of the practical, I have created database called practical and collection called loan. 

> #### <ins>Question 1</ins>
 **Batch Create with minimum 100 records in MongoDb (create batch).**  
> <ins>Query</ins>  
> db.loan.insertMany([ { "Loan_ID": "LP001002", "Gender": "Male", "Married": "No", "Dependents": "0", "Education": "Graduate", "Self_Employed": "No", "ApplicantIncome": 5849, "CoapplicantIncome": 0, "LoanAmount": null, "Loan_Amount_Term": 360, "Credit_History": 1, "Property_Area": "Urban", "Loan_Status": "Y" }, { "Loan_ID": "LP001003", "Gender": "Male", "Married": "Yes", "Dependents": "1", "Education": "Graduate", "Self_Employed": "No", "ApplicantIncome": 4583, "CoapplicantIncome": 1508, "LoanAmount": 128, "Loan_Amount_Term": 360, "Credit_History": 1, "Property_Area": "Rural", "Loan_Status": "N" }, { "Loan_ID": "LP001005", "Gender": "Male", "Married": "Yes", "Dependents": "0", "Education": "Graduate", "Self_Employed": "Yes", "ApplicantIncome": 3000, "CoapplicantIncome": 0, "LoanAmount": 66, "Loan_Amount_Term": 360, "Credit_History": 1, "Property_Area": "Urban", "Loan_Status": "Y" }, { "Loan_ID": "LP001006", "Gender": "Male", "Married": "Yes", "Dependents": "0", "Education": "Not Graduate", "Self_Employed": "No", "ApplicantIncome": 2583, "CoapplicantIncome": 2358, "LoanAmount": 120, "Loan_Amount_Term": 360, "Credit_History": 1, "Property_Area": "Urban", "Loan_Status": "Y" }, { "Loan_ID": "LP001008", "Gender": "Male", "Married": "No", "Dependents": "0", "Education": "Graduate", "Self_Employed": "No", "ApplicantIncome": 6000, "CoapplicantIncome": 0, "LoanAmount": 141, "Loan_Amount_Term": 360, "Credit_History": 1, "Property_Area": "Urban", "Loan_Status": "Y" }, { "Loan_ID": "LP001011", "Gender": "Male", "Married": "Yes", "Dependents": "2", "Education": "Graduate", "Self_Employed": "Yes", "ApplicantIncome": 5417, "CoapplicantIncome": 4196, "LoanAmount": 267, "Loan_Amount_Term": 360, "Credit_History": 1, "Property_Area": "Urban", "Loan_Status": "Y" }, { "Loan_ID": "LP001013", "Gender": "Male", "Married": "Yes", "Dependents": "0", "Education": "Not Graduate", "Self_Employed": "No", "ApplicantIncome": 2333, "CoapplicantIncome": 1516, "LoanAmount": 95, "Loan_Amount_Term": 360, "Credit_History": 1, "Property_Area": "Urban", "Loan_Status": "Y" }, { "Loan_ID": "LP001014", "Gender": "Male", "Married": "Yes", "Dependents": "3+", "Education": "Graduate", "Self_Employed": "No", "ApplicantIncome": 3036, "CoapplicantIncome": 2504, "LoanAmount": 158, "Loan_Amount_Term": 360, "Credit_History": 0, "Property_Area": "Semiurban", "Loan_Status": "N" },    


> **The query continues for all the data. Here there are 614 documents which will inserted in the collection.**  
> Given an array of documents, insertMany() inserts each document in the array into the collection.   

> #### <ins>Question 2</ins>
 **Batch Update with minimum 100 records  in MongoDB (update batch).**
 > db.loan.updateMany({},{$set:{Nationality:'IND'}}) 
 >    
 >* updateMany() updates all matching documents in the collection that match the filter, using the update criteria to apply modifications.  

> #### <ins>Question 3</ins>
 **Perform indexing on particular 3 fields in MongoDB.**
 > db.loan.createIndex({ApplicantIncome :1})   
 > db.loan_dataset.createIndex({Loan_Amount_Term :1})   
 > db.loan_dataset.createIndex({Property_Area:1})  

> #### <ins>Question 4</ins>
 **Find duplicates using aggregation in MongoDB**
 > db.loan_dataset.aggregate([{"$group":{"_id":"$Property_Area","count":{"$sum":1}}},{"$match":{"_id":{"$ne":null},"count":{"$gt":1}}},{"$project":{"Prop":"$_id","_id":0}}]) 

   

