# social-platform-model
This repository contains the code related to the papers 

   - A. Giovanidis, B. Baynat, A. Vendeville - Performance Analysis of Online Social Platforms, INFOCOM 2019.
  
   - A. Giovanidis, B. Baynat, C. Magnien, A. Vendeville - Ranking Online Social Users by their Influence, journal submission 2019.
  
One can find here three Python notebooks:

(1) Notebook "Online+Social+Platform": we produce toy examples of social graphs (grid, ring) with a number of users $N<1000$, and associate each user with a posting and re-posting rate tuple ($\lambda_i$, $\mu_i$). We apply the solution method from the papers above, to derive the influence of each user over the Walls of all others in the network. The solution applies the matrix inversion method, as well as the iterative solution. In this program, the vectors and matrices use np.array matrix structure.

(2) Notebook "SparseOSP": the notebook implements a sparse version of the solution, where matrices A, C and vectors b(i), d(i) are filled in in a sparse way. Also, matrix-vector multiplication profits from the appropriate choice of non-negative entries, and avoids unnecessary multiplications by zero. The program is designed to take as input the Leader Graph and the posting and re-posting activity rates of all the users, that can be estimated by real-world traces. The code can solve for millions of users. We have already tested it for traces with up to 6 Million users and tens of Millions of posts and reposts.

(3) Notebook "OSPemul": this notebook takes as input a real-world trace from a social graph (e.g. Twitter, Weibo) and outputs the influence of each user over all others in the network, as this is calculated directly from the trace. Specifically, the influence of a user i on some other user j, is the percentage of time that posts of origin i are found on the first place of the Wall of user j. To derive the time-intervals of presence, we use the ordered timestamps of posts and reposts. 


Enjoy!
