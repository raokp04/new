Hi All,
I have the following sample data from ORDER table,
ORDER_ID ORDER_DATE ORDER_TYPE1800  1/1/2011 NEW1900  1/2/2013 (NULL)2000  5/7/2014 NEW1900  5/10/2014 NEW 2100  5/11/2014 (NULL)2500  5/30/2014 NEW1900  6/7/2014 USED2300  7/8/2015 NEW1800  5/13/2016 USED2100     6/17/2016  NEW 1600     7/18/2016  NEW1800     8/17/2016  USED
For a given ORDER_ID, I need to find the MIN(ORDER_DATE), ORDER_TYPE where ORDER_TYPE is NOT NULL.
sample SQL -- select min(ORDER_DATE) from ORDER where ORDER_ID = '1900' and ORDER_TYPE is NOT NULL;  Result - 5/10/2014           -- select ORDER_TYPE from ORDER where ORDER_ID = '1900' and ORDER_DATE = '5/10/2014'; Result - NEW     -- update ORDER set ORDER_TYPE = 'NEW' where ORDER_ID = '1900' and ORDER_DATE < '5/10/2014'; 
Use this ORDER_TYPE and populate all the ORDER_TYPE fields where it was NULL for given ORDER_ID.
I am confused on how to achieve this.
The target data should now be,
ORDER_ID ORDER_DATE ORDER_TYPE1800  1/1/2011 NEW1900  1/2/2013 NEW (picked up value from ORDER_DATE = '5/10/2014', earlier it was null)2000  5/7/2014 NEW1900  5/10/2014 NEW 2100  5/11/2014 NEW (picked up value from ORDER_DATE = '6/17/2016', earlier it was null)2500  5/30/2014 NEW1900  6/7/2014 USED2300  7/8/2015 NEW1800  5/13/2016 USED2100     6/17/2016  NEW 1600     7/18/2016  NEW1800     8/17/2016  USED
The above example I demonstrated is for a single order, I need to check and update the ORDER table for thousands of ORDER_ID.
Can anyone please help me in writing an anonymous PL/SQL block that would do it in a single run? If this is not feasible please suggest me which approach would be best?
Thanks,




