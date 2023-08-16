#Hibernate

Credits: * https://www.youtube.com/playlist?list=PLyHJZXNdCXsdC-p2186C6NO4FpadnCC_q
##Annotations in hibernate
   * Entity: Used for model classes to mark them as Entity Beans.
   * Table: Specifing a Table.
   * Access:
   * EmbeddedId: Used for defining composite key.
   * Column: Used to define column name in database.
   * OneToOne/OneToMany/ManyToMany/ManyToOne : Mappings Relations in the schema.
   * Cascade: Cascading the data in the tables.
   * PrmiaryKeyJoinColumn: Used define property for foreign key.

##Hibernate ORM Process
Create POJO clasess -> Create mapping files -> Create configuraton file ->Business logic (Service class) ->Run the application.

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
* New - > session.save(bean) Beans are not present in DB but present in the persistance context.
* Managed -> session.get(bean) All the beans travel through managed state during creation, get(), etc...
* Detached -> session.clear() takes the bean lifecycle to detached state.
* Removed -> sesson.delete(bean) takes the bean to removed state.

####Persistance Context: It contains al the entity beans which are grabbed from DB.


##Transaction:
### Propagation:
* Required: (Default) This propagation is  
* RequiresNew: This is used if the first table entry is used as foreign key in secod table.
* Nested: Only the transaction that failed will be reverted but outer transaction will remain the same.
* Mandatory: If the outer transaction is not marked with @Transaction then the transaction will fail.



