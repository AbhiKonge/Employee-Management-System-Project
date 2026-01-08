There are 2 methods of create join query API in Repository interface (custom query)

-----------------------------------------------------------------------------------------------



##### **Method 1:**

&nbsp;        -using object but it conflict and give nested array

&nbsp;        -there are following steps



**step 1: Repository – Native SQL JOIN**

write a join query in Repository interface using List<Object> datatype

@Query(value="select name,acno,passbook.rddate,passbook.rdamt from rduser inner join passbook \\r\\n"

&nbsp;			+ "on rduser.rid=passbook.rid", nativeQuery = true)

&nbsp;	List<Object\[]> getUserPassbookDetails();



**step 2: Controller**

write a code in controller file 

@GetMapping("/alluserspecificdetails")

&nbsp;	public List<Object\[]> allUserSpecificDetails() {

&nbsp;		List<Object\[]> lst=prepo.getUserPassbookDetails();

&nbsp;		return lst;

&nbsp;	}

---------------------------------------------------------------------------------------------------



##### **Method 2:**

&nbsp;	-using DTO(Data Transfer Object) and service layer 

&nbsp;	-there are following steps



**step 1:  DTO Interface**

create a new package of DTO in this create a interface of DTO and in this interface create a variables of 

fields that you want to show

**Example:**

public interface UserPassbookDTO {

&nbsp;Integer getUid();

&nbsp;String getName();

&nbsp;String getEmail();

&nbsp;Double getRdamt();

&nbsp;LocalDate getRddate();

}



**Step 2: Repository – Native SQL JOIN**

write a join query in Repository interface using List<DTOInterface> datatype

**Example:**

@Query(value="select name,acno,passbook.rddate,passbook.rdamt from rduser inner join passbook "

&nbsp;			+ "on rduser.rid=passbook.rid", nativeQuery = true)

&nbsp;	List<UserPassbookDTO> getUserPassbookDetails();



**Step 3: Controller**

write a code in controller file

**Example:**

@GetMapping("/details")

&nbsp;	public List<UserPassbookDTO> allUserDetails(){

&nbsp;		List<UserPassbookDTO> lst=prepo.getUserPassbookDetails();

&nbsp;		return lst;

&nbsp;	}



























































