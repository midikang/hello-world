spring exception and solution
============================


No transactional EntityManager available
----------
  
    Hibernate: select pettype0_.id as id1_3_, pettype0_.name as name2_3_ from types pettype0_ order by pettype0_.name
    WARN  warn - Handler execution resulted in exception
    javax.persistence.TransactionRequiredException: No transactional EntityManager available
    	at org.springframework.orm.jpa.SharedEntityManagerCreator$SharedEntityManagerInvocationHandler.invoke(SharedEntityManagerCreator.java:275) 
    	at com.midi.samples.petclinic.repository.jpa.JpaPetRepository.save(JpaPetRepository.java:35) 
    	at com.midi.samples.petclinic.service.ClinicServiceImpl.savePet(ClinicServiceImpl.java:53) 

Solution
--------
Add @Transactional on method savePet.


typeMismatch
--------
  org.springframework.validation.BeanPropertyBindingResult: 1 errors
  Field error in object 'pet' on field 'Type': rejected value [bird]; codes [typeMismatch.pet.Type,typeMismatch.Type,typeMismatch.com.midi.samples.petclinic.model.PetType,typeMismatch]; arguments [org.springframework.context.support.DefaultMessageSourceResolvable: codes [pet.Type,Type]; arguments []; default message [Type]]; default message [Failed to convert property value of type 'java.lang.String' to required type 'com.midi.samples.petclinic.model.PetType' for property 'Type'; nested exception is java.lang.IllegalStateException: Cannot convert value of type [java.lang.String] to required type [com.midi.samples.petclinic.model.PetType] for property 'Type': no matching editors or conversion strategy found]
  
Solution  
--------
* Create PetTypeFormatter by implementing Formatter interface.
* Add Register PetTypeFormatter bean.
* 

ownerId is null after execute saveOwner method
--------
Hava you set InitBinder for WebDataBinder?

incompatible data type in conversion: from SQL type DATE to
--------
11:33:02.736 [tomcat-http--3] DEBUG org.hibernate.loader.Loader - Result row: EntityKey[com.midi.samples.petclinic.model.Owner#1], EntityKey[com.midi.samples.petclinic.model.Pet#1]
11:33:02.972 [tomcat-http--3] DEBUG o.h.e.jdbc.spi.SqlExceptionHelper - could not execute query [select owner0_.id as id1_0_0_, pets1_.id as id1_1_1_, owner0_.first_name as first_na2_0_0_, owner0_.last_name as last_nam3_0_0_, owner0_.address as address4_0_0_, owner0_.city as city5_0_0_, owner0_.telephone as telephon6_0_0_, pets1_.name as name2_1_1_, pets1_.birth_date as birth_da3_1_1_, pets1_.owner_id as owner_id4_1_1_, pets1_.type_id as type_id5_1_1_, pets1_.owner_id as owner_id4_0_0__, pets1_.id as id1_1_0__ from owners owner0_ left outer join pets pets1_ on owner0_.id=pets1_.owner_id where owner0_.last_name like ?]
java.sql.SQLSyntaxErrorException: incompatible data type in conversion: from SQL type DATE to [B, value: instance of org.hsqldb.types.TimestampData

solution
--------

    @Column(name = "birth_date")
    @Type(type = "org.jadira.usertype.dateandtime.joda.PersistentDateTime")
    @DateTimeFormat(pattern = "yyyy/MM/dd")
    private DateTime birthDate;
