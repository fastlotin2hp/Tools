#  introduction

  ## reviewing Bash
   - **cat head tail more** *.txt
  ## Tilde and Brace
   - **echo ~-** last directory
   - **touch** {a.txt, b.txt, c.txt}  
   - **touch** file_{1..10..2} 1 to 10 step of 2
   - **touch** file_{A..z..2} A to z step of 2
   - **ls -1| wc -l** count how many files
	## pipes and redirection
	 - **ls |more**
	 - **cp a b 1> success.txt 2> error.txt ** same as - **cp a b &> output.txt **
	 - **1>** the success message
	 - **2>** the error message
	 - **&>** both success and error message
	 - **ls > /dev/null** no print out
    
