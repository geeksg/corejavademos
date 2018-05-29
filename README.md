# sample/*********************************************************************************
 * File                 : Consumer_Electricity_Charges.txt
 * Author Name          : Vidya chitla
 * Version              : 1.0
 * Last Modified Date   : 8-05-2018
 * Description          : Program to calculate the Consumer_Electricity_Charges
 **********************************************************************************/

RECORD Consumer_Electricity_Charges
	DECLARE Consumer_no AS INTEGER   	
	DECLARE Consumer_name AS STRING
	DECLARE no_of_unit AS DOUBLE
	DECLARE first_unit AS DOUBLE
	INITILIZE first_unit IS 02.96		// initialize the first 100 unit charging amount 
`	DECLARE above_unit AS DOUBLE
	INITILIZE above_unit IS 05.56		// initialize the above 100 unit charging amount 
	DECLARE calc_amt AS DOUBLE	
END RECORD

BEGIN
	/*Get the Consumer Name,Number and number of Units*/
	ACCEPT "Enter the consumer no" AS Consumer_no 		
	ACCEPT "Enter the consumer name" AS Consumer_name 
	ACCEPT "Enter the no of unit" AS no_of_unit 
	calc_amt = calc_bill()			//call the calc_bill function
	display_bill()				//call the display_bill function
END


/*********************************************************************
* Module Name         	: calc_bill()
* Author                : Vidya chitla
* Return Type           : DOUBLE
* Creation Date         : 08-05-2017
* Description           : calculate the Consumer_electricity_bill
 *********************************************************************/


SUB calc_bill()
	
	IF no_of_unit <100 THEN
		calc_amt = no_of_unit * first_unit  
	ELSE IF no_of_unit >=100	
		calc_amt = no_of_unit * above_unit 
	ELSE IF no_of_unit == " "
		EXCEPTION			//The no of unit is empty it throws an exception
			WHEN NoSuchElement THEN
				calc_amt ="Enter the no of unit"  
		END EXCEPTION 
	END IF
	RETURN calc_amt 
		
END SUB



/*********************************************************************
* Module Name         	: display_bill()
* Author                : Vidya chitla
* Creation Date         : 08-05-2017
* Description           : calculate the Consumer_electrical_bill
 *********************************************************************/

SUB display_bill()
	PRINT "Consumer No" IS Consumer_no 
	PRINT "Consumer Name" IS Consumer_name 
	PRINT "Consumer No of unit" IS no_of_unit 
	PRINT "Consumer Total amount IS calc_amt
END SUB
	
