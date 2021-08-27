
In this solution, the employee hierarchy is modelled as a directed acyclic graph DAG.

The graph data structure seemed to me like a natural fit for the problem domain in addition to providing powerful algorithms for traversal.

Employees are modelled as Vertices and the relationship between them as Edges.

To ensure that an employee does not report to more than one manager, I limited the number of incoming edges to any vertext to a maximum of 1 and a minimum of 0 in the case of the CEO who has no supervisor.

Each employee is added to a dictionary data structure which ensures that there are no duplicate values.

I validate the salary of each employee to ensure it is a valid integer.

I construct the graph from the dictionary thus guaranteeing that each manager is first listed as an employee.

The acyclic nature of the DAG ensures that there is no double linking between employees. To ensure this, I do a Depth First Traversal DFS of the graph begining at the source Vertex of an Edge, if the manager exists among the child nodes, then adding the edge would cause a cycle, hence I don't add it.

To get the Salary Budget for any manager, I do a DFS begining at the manager Vertext and sum all the salaries in the generated path.

Input
The list of employees is supplied as a text file.

The sample employee hierarchies are found in the UnitTests/ folder.

Output
The program makes output in the following format. This sample output is taken from running it on the test.txt input file with Employee1 as the manager of interest.

It outputs 3300 the total salary budget of the CEO who is Employee1 in this case.
