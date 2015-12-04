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
