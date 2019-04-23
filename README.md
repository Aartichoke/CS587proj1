Description
The scope of this portion of the project is to create a data generation script that conforms to the Wisconsin Benchmark, create a database instance, define a schema based on the Wisconsin Benchmark format, and upload the data to the newly created database.
System
This database is hosted on a MySQL MariaDB 10.0 instance on a cloud backend.  This cloud backend is a corporate system that is not publicly accessible. To interface with this system, I am using MySQL Workbench, which is a Windows based SQL management GUI.
Generating Data
Generating the data specified in the Wisconsin Benchmark paper is done with a Python 2.7 script. This data is printed in a CSV format to a file. The first row is are the attribute names, followed by data that meets the standards for the paper. For the purpose of this project portion, a tuple size of 1000 is used. 
The convert function from the Wisconsin Benchmark is adapted for this script in a Python format. The code may be viewed for further specific details.
Loading Data
The data is uploaded using Workbench. The CSV and be directly uploaded using the CSV import tool. This function is also configured to ignore primary key duplicate errors. Due to duplicate primary keys, 650 total entries were able to be uploaded to the database. This same method is followed for each table creation. 
Lessons
There are two major lessons to be learned from this implementation. First, adapting the sample code was difficult and took multiple iterations due to the source changing. The paper did not specify what the ideal case should be, but only insisted the example code should be used. The issue was that the example code was not bug free, and it was difficult to determine what the exact output should be.
Secondly, 1000 tuples for an upload takes over twenty minutes with my current method. A better implementation would be to write a SQL script that uses server-side procedures to generate and insert the data. This would eliminate the need for a lengthy upload, and would be useful for tuple counts of larger magnitude. 
 
Appendix A: Table Creation
CREATE TABLE `DBTest3`.`table2` (
  `unique1` INT NOT NULL,
  `unique2` INT NOT NULL,
  `two` INT NOT NULL,
  `four` INT NOT NULL,
  `ten` INT NOT NULL,
  `twenty` INT NOT NULL,
  `onePercent` INT NOT NULL,
  `tenPercent` INT NOT NULL,
  `twentyPercent` INT NOT NULL,
  `fiftyPercent` INT NOT NULL,
  `unique3` INT NOT NULL,
  `evenOnePercent` INT NOT NULL,
  `oddOnePercent` INT NOT NULL,
  `stringu1` VARCHAR(127) NOT NULL,
  `stringu2` VARCHAR(127) NOT NULL,
  `string4` VARCHAR(127) NOT NULL,
  PRIMARY KEY (`unique1`));
 
Appendix B: Database contents
SELECT * FROM DBTest3.table2 LIMIT 0, 50
2, 213, 0, 2, 2, 2, 2, 2, 2, 0, 2, 4, 5, AAAAAACXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAIFXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
4, 54, 0, 0, 4, 4, 4, 4, 4, 0, 4, 8, 9, AAAAAAEXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAACCXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
5, 756, 1, 1, 5, 5, 5, 5, 0, 1, 5, 10, 11, AAAAAAFXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABDCXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
7, 228, 1, 3, 7, 7, 7, 7, 2, 1, 7, 14, 15, AAAAAAHXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAIUXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
8, 720, 0, 0, 8, 8, 8, 8, 3, 0, 8, 16, 17, AAAAAAIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABBSXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
10, 738, 0, 2, 0, 10, 10, 0, 0, 0, 10, 20, 21, AAAAAAKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABCKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
12, 50, 0, 0, 2, 12, 12, 2, 2, 0, 12, 24, 25, AAAAAAMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAABYXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
13, 963, 1, 1, 3, 13, 13, 3, 3, 1, 13, 26, 27, AAAAAANXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABLBXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
14, 298, 0, 2, 4, 14, 14, 4, 4, 0, 14, 28, 29, AAAAAAOXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAALMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
15, 139, 1, 3, 5, 15, 15, 5, 0, 1, 15, 30, 31, AAAAAAPXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAFJXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
19, 12, 1, 3, 9, 19, 19, 9, 4, 1, 19, 38, 39, AAAAAATXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAAMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
20, 902, 0, 0, 0, 0, 20, 0, 0, 0, 20, 40, 41, AAAAAAUXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABISXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
21, 20, 1, 1, 1, 1, 21, 1, 1, 1, 21, 42, 43, AAAAAAVXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAAUXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
22, 709, 0, 2, 2, 2, 22, 2, 2, 0, 22, 44, 45, AAAAAAWXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABBHXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
23, 603, 1, 3, 3, 3, 23, 3, 3, 1, 23, 46, 47, AAAAAAXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAXFXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
25, 33, 1, 1, 5, 5, 25, 5, 0, 1, 25, 50, 51, AAAAAAZXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAABHXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
26, 295, 0, 2, 6, 6, 26, 6, 1, 0, 26, 52, 53, AAAAABAXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAALJXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
27, 143, 1, 3, 7, 7, 27, 7, 2, 1, 27, 54, 55, AAAAABBXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAFNXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
30, 200, 0, 2, 0, 10, 30, 0, 0, 0, 30, 60, 61, AAAAABEXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAHSXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
32, 25, 0, 0, 2, 12, 32, 2, 2, 0, 32, 64, 65, AAAAABGXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAAZXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
33, 186, 1, 1, 3, 13, 33, 3, 3, 1, 33, 66, 67, AAAAABHXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAHEXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
34, 612, 0, 2, 4, 14, 34, 4, 4, 0, 34, 68, 69, AAAAABIXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAXOXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
36, 533, 0, 0, 6, 16, 36, 6, 1, 0, 36, 72, 73, AAAAABKXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAUNXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
37, 297, 1, 1, 7, 17, 37, 7, 2, 1, 37, 74, 75, AAAAABLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAALLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
39, 887, 1, 3, 9, 19, 39, 9, 4, 1, 39, 78, 79, AAAAABNXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABIDXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
40, 137, 0, 0, 0, 0, 40, 0, 0, 0, 40, 80, 81, AAAAABOXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAFHXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
42, 136, 0, 2, 2, 2, 42, 2, 2, 0, 42, 84, 85, AAAAABQXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAFGXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
43, 444, 1, 3, 3, 3, 43, 3, 3, 1, 43, 86, 87, AAAAABRXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAARCXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
44, 310, 0, 0, 4, 4, 44, 4, 4, 0, 44, 88, 89, AAAAABSXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAALYXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
45, 586, 1, 1, 5, 5, 45, 5, 0, 1, 45, 90, 91, AAAAABTXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAWOXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
46, 707, 0, 2, 6, 6, 46, 6, 1, 0, 46, 92, 93, AAAAABUXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABBFXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
47, 438, 1, 3, 7, 7, 47, 7, 2, 1, 47, 94, 95, AAAAABVXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAQWXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
48, 751, 0, 0, 8, 8, 48, 8, 3, 0, 48, 96, 97, AAAAABWXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABCXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
49, 824, 1, 1, 9, 9, 49, 9, 4, 1, 49, 98, 99, AAAAABXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABFSXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
50, 640, 0, 2, 0, 10, 50, 0, 0, 0, 50, 100, 101, AAAAABYXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAYQXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
52, 392, 0, 0, 2, 12, 52, 2, 2, 0, 52, 104, 105, AAAAACAXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAPCXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
53, 595, 1, 1, 3, 13, 53, 3, 3, 1, 53, 106, 107, AAAAACBXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAWXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
54, 435, 0, 2, 4, 14, 54, 4, 4, 0, 54, 108, 109, AAAAACCXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAQTXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
56, 903, 0, 0, 6, 16, 56, 6, 1, 0, 56, 112, 113, AAAAACEXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABITXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
57, 692, 1, 1, 7, 17, 57, 7, 2, 1, 57, 114, 115, AAAAACFXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABAQXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
58, 570, 0, 2, 8, 18, 58, 8, 3, 0, 58, 116, 117, AAAAACGXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAVYXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
59, 152, 1, 3, 9, 19, 59, 9, 4, 1, 59, 118, 119, AAAAACHXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAFWXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
61, 572, 1, 1, 1, 1, 61, 1, 1, 1, 61, 122, 123, AAAAACJXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAWAXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
63, 427, 1, 3, 3, 3, 63, 3, 3, 1, 63, 126, 127, AAAAACLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAQLXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
68, 454, 0, 0, 8, 8, 68, 8, 3, 0, 68, 136, 137, AAAAACQXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAARMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, OOOOxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
69, 105, 1, 1, 9, 9, 69, 9, 4, 1, 69, 138, 139, AAAAACRXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAEBXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
70, 771, 0, 2, 0, 10, 70, 0, 0, 0, 70, 140, 141, AAAAACSXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAABDRXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
71, 15, 1, 3, 1, 11, 71, 1, 1, 1, 71, 142, 143, AAAAACTXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAAPXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, VVVVxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
72, 376, 0, 0, 2, 12, 72, 2, 2, 0, 72, 144, 145, AAAAACUXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAAOMXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
76, 65, 0, 0, 6, 16, 76, 6, 1, 0, 76, 152, 153, AAAAACYXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, AAAAACNXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX, HHHHxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
