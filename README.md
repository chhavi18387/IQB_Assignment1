## Question 1: Reading PDB and extracting data:
- In the given question we were to implement a program that computes the Header, Title  and Resolution from a given pdb file that is reading through the protein data bank file. 
So we have input format as a given PDB file, and we need to store the following details in  a text file. 
- Brief Code Implementation: 
First of all, we use sys to read the input and output files through the command line.After  that we open the input and output file. Then we start reading each line from the pdb file,  and as we are reading a line we are checking for our needed computations that makes  the algorithm efficient. So after reading a line, we split it on the basis of the first word,  then we check if the first word is Header, Title or Remark. If it is Header then , we write  the name corresponding to the header in our output file. Similar process is followed for  the title. Now if we find our splitted word as Remark then we proceed in the line to check  if we find the word Resolution and if we reach it, we write the value corresponding next to  resolution in Angstroms. 

*Input Format    PDB file .For example, 5yud.pdb*


*Output Format  Text file named as Output_file_2.txt containing the details of Header, Title and Resolution  from the protein databank file.*


*How to run?* 

      python3 iqb1_q2.py -i 5yud.pdb -o output_file_2.txt 
      
  
 
- Note:- 
In the pdb file there were two values corresponding to Resolution under the Remark  section named as Resolution and Effective Resolution, but since both values were same  therefore we stored the value of Resolution in the output file

## Question 2: Needleman Wunsch (Aligning two protein sequences using dynamic programming):
We use dynamic programming to align two sequences given in the FASTA format. At first,  two sequences are read out from the given FASTA file, ignoring the headers. These  sequences are then used for the following: 

- Dotplot :
The sequences (seq1 and seq2) are used to create a dot plot that shows the  matches between two sequences. We create a |seq2| x |seq1| matrix and mark  the cell (i, j) with an asterisk (*) to denote that i​th​ character of the seq2 is the same  as j​th ​character of seq1. If not, the cell is marked with an empty string. 
 
 
- Calculation of Sum-Matrix : 
After the dot plot has been plotted, we calculate the sum matrix. In the original  form of the dot-plot, the asterisk is stored as 1 and empty string as 0. We calculate  the value of the (i, j) cell as follows:
                
                cell(i, j) = cell(i, j) + max(cell(i+1, j+1),
                                  cell(i+1, j+2 to |seq1|),
                                  cell(i+2 to |seq2|, j+1)) 
 
 
- Recognizing the maximum Length : 
After the sum matrix has been created, the length of the longest possible  alignment is calculated. This is done by finding out the maximum value stored in  one of the cells of the sum matrix.

- Back Tracing :
Starting from the cell with the maximum value, we go back, tracing back the path  that got us to the maximum value. For each movement downwards or to the right,  the value corresponding to the sequences are stored to form a new sequence. At  the end of this function, optimally aligned protein sequence is returned. 

*Input Format  FASTA file containing two protein sequences.*


*Output Format  Text file containing the DOTPLOT, sum matrix and the alignment of the given sequences.  The same value are printed on the terminal too.*


*How to run?* 

       python3 iqb1_q3.py -i protein.fa -o output_file_3.txt  









Contributors: Chhavi , Dibya , Himanshi
