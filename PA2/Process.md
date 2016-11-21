####Application of 3NF Synthesis Algorithm

Determined key = (emp_no, title)

**A. Translate Given FD's:** 

1. If you know the department number you know the deparment name. 

        (dept_no) -> (dept_name)

2. There can only be one dept manager at the same time. 
   
        (emp_no, dept_no) -> (dept_mgr_from_date, dept_mgr_to_date)
   
3. Each employee can only hold one title at the same time.

        (emp_no, title) -> (title_from_date, title_to_date)

**B. Find Minimal Basis:**

1. Split all RHS

        (dept_no) -> (dept_name)
        (emp_no, dept_no) -> (dept_mgr_from_date)
        (emp_no, dept_no) -> (dept_mgr_to_date)
        (emp_no, title) -> (title_from_date)
        (emp_no, title) -> (title_to_date)
        
2. Test for minimality LHS where # attributes >= 2

        Necessarily, (emp_no, dept_no) and (emp_no, title) are minimal.
        
3. Test for minimality RHS (will leave process to reader). After splitting RHS compute closure of each LHS excluding one of the RHS FD's. If the closure is incomplete then we know that the RHS is minimal because each split FD is required.

        (dept_no) -> (dept_name) is minimal.
        (emp_no, dept_no) -> (dept_mgr_from_date, dept_mgr_to_date) is minimal.
        (emp_no, title) -> (title_from_date, title_to_date) is minimal.
        
4. Collect Similar LHS to form FD's that make a minimal basis.

        (dept_no) -> (dept_name)
        (emp_no, dept_no) -> (dept_mgr_from_date, dept_mgr_to_date)
        (emp_no, title) -> (title_from_date, title_to_date)
        
**C. Make a relation of the attributes of each FD of the Minimal Basis. The RHS of the FD is the new key for the relation.**

        R1 = (*dept_no*, dept_num)
        R2 = (*emp_no*, *dept_no*, dept_mgr_from_date, dept_mgr_to_date)
        R3 = (*emp_no*, *title*, title_from_date, title_to_date)
        
**D. X -> A violates 3NF IFF: X is not a superkey, and also A is not prime**

        There are no 3NF violations in the above relations so the 3NF synthesis is complete.
