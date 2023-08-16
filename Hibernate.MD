#Hibernate

Credits: * https://www.youtube.com/playlist?list=PLyHJZXNdCXsdC-p2186C6NO4FpadnCC_q
##Annotations in hibernate
   * Entity: Used for model classes to mark them as Entity Beans.
   * Table: Specifying a Table.
   * Access:
   * EmbeddedId: Used for defining composite key.
   * Column: Used to define column name in database.
   * OneToOne/OneToMany/ManyToMany/ManyToOne : Mappings Relations in the schema.
   * Cascade: Cascading the data in the tables.
   * PrimaryKeyJoinColumn: Used to define property for foreign key.

##Hibernate ORM Process
Create POJO classes -> Create mapping files -> Create configuration file ->Business logic (Service class) ->Run the application.

##Session get() vs load()
Get() method follows instant loading, whereas load() method follows lazy loading.

##Hibernate Cache:
* First level cache
   first level cache is by default, The data is not visible to other sessions, on session close without save the data will be lost.
   It improves performance, one can clear or evict the cache.
* Second level cache:
   Explicitly configured to use it.
   Different types of second level caches are there.
* Query cache:

##Entity Lifecycle and states:
* New - > session.save(bean) Beans are not present in DB but present in the persistence context.
* Managed -> session.get(bean) All the beans travel through managed state during creation, get(), etc...
* Detached -> session.clear() takes the bean lifecycle to detached state.
* Removed -> session.delete(bean) takes the bean to removed state.

####Persistence Context: It contains al the entity beans which are grabbed from DB.


##Transaction:
### Propagation:
* Required: (Default) This propagation is  
* RequiresNew: This is used if the first table entry is used as foreign key in second table.
* Nested: Only the transaction that failed will be reverted but outer transaction will remain the same.
* Mandatory: If the outer transaction is not marked with @Transaction then the transaction will fail.
* NotSupported: If the current transaction exists, first Spring suspends it, and then the business logic is executed without a transaction.
* Supports: Allows both transaction or not (flexible).

## Hibernate N+1 problem.
####Problem 
The problem with hibernate queries is that if the data is nested i.e Table1 has Table2, intern Table has Table3 then hql queries are fired with 3(N+1) where 3 is for tables and N is for records in each table.
If the table rows dramatically increases then the queries are too many to process. This drains the performance of the
application.
####Solution
We need to use 
* Left Join and fetch mechanism 
* Entity Graphs; available in both Hql and Spring JPA 2.1 to overcome this problem.
Eg: Departments has Employees, and Employees has Accounts.
Ans:
```
@Query("Select p form Department p left join fetch p.listOfEmployees")
List<Department> findWithoutNPlusOne();

@EntityGraph(attributePaths ={"listOfEmployees"})
List<Employee> findAll();
```


