# social-platform-model
This repository contains the code related to the papers 

   - A. Giovanidis, B. Baynat, A. Vendeville - Performance Analysis of Online Social Platforms, INFOCOM 2019. DOI: 10.1109/INFOCOM.2019.8737539
  
   - A. Giovanidis, B. Baynat, C. Magnien, A. Vendeville - Ranking Online Social Users by their Influence, IEEE/ACM Transactions on Networking, 2021. DOI 10.1109/TNET.2021.3085201
  
One can find here four Python notebooks:

(1) Notebook "Online+Social+Platform": we produce toy examples of social graphs (grid, ring) with a number of users $N<1000$, and associate each user with a posting and re-posting rate tuple ($\lambda_i$, $\mu_i$). We apply the solution method from the papers above, to derive the influence of each user over the Walls of all others in the network. The solution applies the matrix inversion method, as well as the iterative solution. In this program, the vectors and matrices use np.array matrix structure.

(2) Notebook "SparseOSP": the notebook implements a sparse version of the solution, where matrices A, C and vectors b(i), d(i) are filled in in a sparse way, using dictionary structure. Also, matrix-vector multiplication profits from the appropriate choice of non-negative entries, and avoids unnecessary multiplications by zero. The program is designed to take as input the Leader Graph and the posting and re-posting activity rates of all the users, that can be estimated by real-world traces. The code can solve for millions of users. We have already tested it for traces with up to 1,3 Million users and tens of Millions of posts and reposts.

(3) Notebook "OSPemul": this notebook takes as input a real-world trace from a social graph (e.g. Twitter, Weibo) and outputs the influence of each user over all others in the network, as this is calculated directly from the trace. Specifically, the influence of a user i on some other user j, is the percentage of time that posts of origin i occupy the first place of the Wall of user j. To derive the time-intervals of post presence, we make use of the ordered timestamps of posts and reposts. 

(4) Notebook "SimulatorOSP": the notebook presents a discrete-event simulator, that can generate a synthetic trace of tweets in the form (tweetID, timestamp, userID, retweetID) that can be used as input for the "OSPemul" notebook, to determine the empirical PSI-score. The Simulator can consider different inter-arrival distributions, as well as different post selection and eviction policies on the Walls and Newsfeeds. We use it to verify in the papers the validity of the model. 


We have used as input for the above programs, traces from:

   Twitter: freely available  https://www.kaggle.com/borisch/russian-election-2018-twitter
   This trace comes from the Russian elections. It contains 181K active users, with 674K original Tweets and 1,27M Retweets.
   
   
   Weibo: freely available  https://aminer.org/influencelocality
   This trace emphasizes on users that are highly retweeted and can be useful to study cascade effects. It contains 1,3M active users with 233K original posts and 33,3M Retweets. It was originally collected and used in the work:
   
   Jing Zhang, Biao Liu, Jie Tang, Ting Chen, and Juanzi Li. Social Influence Locality for Modeling Retweeting Behaviors. In Proceedings of the 23rd International Joint Conference on Artificial Intelligence (IJCAI'13). pp. 2761-2767.

Some preprocessing - not included here - is necessary to bring the traces to the appropriate input form (per line):

   TweetID, Timestamp, UserID, RetweetID


Enjoy!
