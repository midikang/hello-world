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
