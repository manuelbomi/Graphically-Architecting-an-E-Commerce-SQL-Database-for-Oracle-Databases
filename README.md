# Graphically Architecting an E-Commerce SQL Database for Oracle Databases   



### **OVERVIEW**
Reliably architecting databases is very crucial for designing efficient data analytics systems. After selecting the software and the database to be used for a system, the next important question is to decide on how to architect the database, and how to correctly specify the relationships between the entities in the database. To do this all-important architecting task, entity relationship diagrams (ERDs) are often used. 

After the data/system architect have specified the tables and their relationships, the modeler, database engineer, software engineer and/or the data engineer will then translate the ERD into SQL codes to create the desired database and tables for the target database. 

> [!NOTE]
> In some companies, the duties or tasks assigned to the data architect, system architect, data modeler, database engineer, data engineer or software engineer may ovelap. In most cases however, these engineers must often work hand-in-hand to achieve the desired objectives. 
---

### **Benefits of Using Lucidchart for Entity Relationship Diagrams**
For very complex systems, due to system intricacies and the number of engineers that may be involved in the system design, there may be errors, bugs or mismatches that are not easily detected between the architected system  and the final designed database. This is where the benefit(s) of using Lucidchart for architecting complex can be realized. Lucidchart is a visual collaborative software that everyone within a project can access, contribute to the ERDs and share the ERD updates among the team members.

In addition, Lucidchart can be used to shrink or eliminate an important step between architecting the system using ERDs and translating the archittected system to SQL codes for the target database. Eliminating this step can lead to reduction in mismatches or errors between the architected system and the final designed database. 

---

> [!IMPORTANT]
After using Lucidchart to architect the system using ERDs, Lucidchart can then be used to automatically generate SQL codes relating to the ERD for the target database. This step can serve to reduce errors or mismatches between the architected system and the designed database.
>

---
In this discourse, we will show (using infographs) how to use Lucidchart to architect an e-commerce database comprising of four tables viz: customers, products, orders and order_details tables.

We shall then show how to use Lucidchart to translate the e-commerce ERD to a database by using Lucidchart to automatically generate SQL codes for Oracle 21c database. 

---
> [!IMPORTANT]
Here, we have shown the steps needed to efficiently architect an e-commerce database for Oracle 21c database using SQLDeveloper front end for the Oracle 21c database.
>
---


Step 1: Register free version LucidChart
---
![Image](https://github.com/user-attachments/assets/0d68a670-3833-448f-ba65-add57af15568)


---
Step 2: Click on 'Documents'. Click New, LucidChart, Start Diagramming.
---
![Image](https://github.com/user-attachments/assets/8ca6e2a8-2bec-4360-98c8-60c48fc26b9d)

---
Step 3:  Click New, LucidChart, Start Diagramming.
![Image](https://github.com/user-attachments/assets/049f1541-fb2a-4972-b2cf-02257a967879)
---

![Image](https://github.com/user-attachments/assets/600b3c3c-6095-4ab5-964b-759f2cde5d6b)

---
![Image](https://github.com/user-attachments/assets/72808a07-1297-4b10-8f0d-a38b4ca9e5e5)

---
Step 4: Search for ERD
---
![Image](https://github.com/user-attachments/assets/aba67e24-7349-43e4-b338-e6b771a01171)
---

Step 5: The Lucidchart ERD will reveal four ways to create an ERD. 
---
![Image](https://github.com/user-attachments/assets/74299c57-c31f-4821-960a-bd2ebba1b9da)

---
Step 6: The 'Key', 'Field', 'Type' (3 columns) ERD type is selected for our e-commerce use case. 
---
In this use case, four tables viz: customers, products, orders, and order_details were created. 
Relationship links such as one-to-many and many-to-one are used extensively to establish relationships between the tables. 
---

![Image](https://github.com/user-attachments/assets/75cf861e-9fb6-4ab1-952f-2b569dc626ec)

---
You can export the created ERD as png, jpeg, svg etc; to include in your report, slide or repository
---
![Image](https://github.com/user-attachments/assets/011480b1-7946-4561-a911-162fbaf412b9)
---

Step 7: After creating the ERD and establishing links, select all the tables and relations links in the ERD. 
Click on 'Export ERD'
---
![Image](https://github.com/user-attachments/assets/b481af2f-be10-457e-9f62-64e2d97ce019)

---
Step 8: Click on 'Export ERD'. In the current Lucidchart version, SQL codes for the ERD can only be generated for PostgreSQL, MySQL, Quickbase, Microsoft SQL Server and Oracle Database. For other relational type databases such as Teradata, Snowflakes etc, slight tweeks can be made to the generated SQL codes to create the tables in the desired database.
You can then copy the code for your target database, create the database, paste the code into the query run tab of your target database, and use the SQL code to create the tables.
---
Ensure that you select the button for the Oracle database variant of the ERD code
![Image](https://github.com/user-attachments/assets/46c897e4-3c68-4500-a640-140271ca95e9)

---


> [!TIP]
> Here, we have shown the e-commerce use case SQL code generated by Lucidchart for Oracle 21c database.
> Note that in the customer table code, Oracle 21c was generating errors due to the presence of the "is_active" BOOLEAN column. Hence the column was removed. 

> Oracle Database Implementation

```ruby
'CREATE TABLE "customer" (
  "customer_id" INT ,
  "last_name" VARCHAR(255),
  "first_name" VARCHAR(255),
  "phone_nos" VARCHAR(20),
  "email" VARCHAR(255),
  "street" VARCHAR(255),
  "city" VARCHAR(255),
  "zip" VARCHAR(255),
  PRIMARY KEY ("customer_id")
);

CREATE TABLE "products" (
  "product_id" INT,
  "product_name" VARCHAR(255),
  "price" DECIMAL,
  PRIMARY KEY ("product_id")
);

CREATE TABLE "order" (
  "id" INT,
  "customer_id" INT,
  "date" DATE,
  PRIMARY KEY ("id"),
  CONSTRAINT "FK_order.customer_id"
    FOREIGN KEY ("customer_id")
      REFERENCES "customer"("customer_id")
);

CREATE TABLE "order_detail" (
  "id" INT,
  "order_id" INT,
  "product_id" INT,
  "quantity" INT,
  "price" DECIMAL(12, 2),
  "to_street" VARCHAR(255),
  "to_city" VARCHAR(255),
  "to_zip" VARCHAR(255),
  "ship_date" VARCHAR(255),
  PRIMARY KEY ("id"),
  CONSTRAINT "FK_order_detail.product_id"
    FOREIGN KEY ("product_id")
      REFERENCES "products"("product_id"),
  CONSTRAINT "FK_order_detail.order_id"
    FOREIGN KEY ("order_id")
      REFERENCES "order"("id")
);

```


---
Step 9: Log into your Oracle 21c database using the Sqldeveloper front end. Use your specified credentials (username/password) to log in. Specify the name of the database to be created
---
 
![Image](https://github.com/user-attachments/assets/d4b75202-49ab-47bc-9fd9-1c1ff037bacf)

---
Step 10: Click on your database to reveal the query run tool interface
---
![Image](https://github.com/user-attachments/assets/f1c70826-fe53-4a8b-8b59-1f938713c0f5)

---
Step 11: Copy and paste the gennerated ERD code onto the query run tool pad. Create the tables one after the other so as to be able to easily track error sources. Create "customers table"
---
![Image](https://github.com/user-attachments/assets/c9af75f3-5fca-4cdf-8d04-fb4dc677ac39)
---
Step 12: Create "products" table
---
![Image](https://github.com/user-attachments/assets/62bf27d4-bd1e-453b-890c-96e49886d36e)

---
Step 13: Create "orders" table
---
![Image](https://github.com/user-attachments/assets/855b3387-4697-4b83-96ed-5a7ef69aea0d)

---
Step 14: Create "order_details" table
---
![Image](https://github.com/user-attachments/assets/24b8bb42-8799-4bf1-9a5f-7bcf6df07fc6)



### **AUTHOR'S BACKGROUND**

```

Author's Name:  Emmanuel Oyekanlu
Skillset:   I have experience spanning several years in developing scalable enterprise data pipelines, architecting enterprise data solutions,
data engineering, high performance computing (GPU, CUDA), machine learning, NLP and LLM applications as well as deploying scalable solutions (apps) on-prem and in the cloud.
I can be reached through: manuelbomi@yahoo.com
Website:  http://emmanueloyekanlu.com/
Publications:  https://scholar.google.com/citations?user=S-jTMfkAAAAJ&hl=en
LinkedIn:  https://www.linkedin.com/in/emmanuel-oyekanlu-6ba98616
Github:  https://github.com/manuelbomi

```
[![Icons](https://skillicons.dev/icons?i=aws,azure,gcp,scala,mongodb,redis,cassandra,kafka,anaconda,matlab,nodejs,django,py,c,anaconda,git,github,mysql,docker,kubernetes&theme=dark)](https://skillicons.dev)


