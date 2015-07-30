

\section{Review of Chaotic Systems and the Lorenz System}

Chaotic systems are deterministic, but are extremely sensitive to initial conditions. This sensitivity of the initial conditions makes long-term prediction of chaotic systems almost impossible unless the initial conditions are known exactly. One of the most famous chaotic systems is the Lorenz system. The Lorenz system is defined by

\begin{equation}
\dot{x} = s(y-x)
\end{equation}
\begin{equation}
\dot{y} = rx - y - xz
\end{equation}
\begin{equation}
\dot{z} = xy - bz
\end{equation}

Lorenz originally formulated these equations to describe atmospheric weather dynamics. The system quickly grew to fame, as emergent chaotic properties of the system became known. The system dynamics of the Lorenz equation depend of the parameters $s,r,b$. For the right choice of the system parameters the solution traces out two the familiar strange attractors. 

\begin{figure}[H]
\centering
\includegraphics[width=0.5\textwidth]{plot1.png}
\caption{The phase space of the Lorenz system is plotted here for the initial conditions $[0,1,0]^T$ and $s = 10$, $r=28$ and $b=\frac{8}{3}$}
\label{figure 3:}
\end{figure}

Many initial conditions will trace out the same strange attractors in phase space for the same parameter values, however the actual values of different solutions will differ dramatically. Figure 2 shows how two solutions with very slightly different initial conditions differ as time increases.

\begin{figure}[H]
\centering
\includegraphics[width=0.5\textwidth]{plot2.png}
\caption{The difference of two solutions of the Lorenz equation with parameters $s = 10$, $r=28$ and $b=\frac{8}{3}$ as a function of time is plotted here. One of the solutions has initial conditions $[0,1,0]^T$ and the other $[0,1,0.01]^T$}
\label{figure 3:}
\end{figure}


\section{Lyapunov Exponents}

As we have seen, solutions of the same chaotic system will diverge quickly even if there is only a very small difference in the initial conditions. The Lyapunov exponents provide a way to quantify this behavior. The Lyapunov exponents are defined as

\begin{equation}
|\delta \mathbf{Z}| \approx e^{\lambda t}|\delta \mathbf{Z_o}|
\end{equation}

where $|\delta \mathbf{Z}|$ is the distance between the two solutions at time $t$, $|\delta \mathbf{Z_o}|$ is the distance of the initial conditions of the solutions and $\lambda$ is the Lyapunov exponent. It is important to note that there is actually a spectrum of Lyapunov exponent as the rate of divergence may differ in different direction. The largest Lyapunov exponent is usually discussed as the Lyapunov exponent since it controls the predictability of the system. The Lyapunov exponent is very hard to find analytically for all but the simplest systems, instead numerical techniques are often used. 

The Lyapunov exponent is intuitively very clear. Negative exponents imply asymptotically stable equilibrium points and stable trajectories, as different solutions converge to each other. A zero exponent implies that the solutions will stay the same distance apart for all time. An example of a system with zero Lyapunov exponents would be a mass on a spring with no damping. A positive exponent usually implies chaos (but other requirements must be met as well). Zooming in on the beginning of figure 2 we clearly see a positive exponent for the Lorenz system. 


\begin{figure}[H]
\centering
\includegraphics[width=0.5\textwidth]{plot3.png}
\caption{The exponential growth of the distance between the two solutions as described in figure 2 is clearly seen here}
\label{figure 3:}
\end{figure}

While figure 3 clearly shows the exponential growth of the distance between two solutions these mysterious 'lumps' appear. The distance in solutions continuously expands and contracts. While the theory of this phenomenon is left out of this summary for the sake of brevity, it is also the reason why systems with positive exponents do not necessarily have to blow up. \cite{Exp}


\section{Subsystems and Synchronous Subsystems}

Louis Pecora and Thomas Carroll showed in 1989 that is possible to synchronize two chaotic systems. Synchronizing systems means that even with different initial conditions, the systems will converge together. Synchronization is thus obviously strongly linked to Lyapunov exponents. Synchronization in chaotic systems would seem impossible at first glance, but Carroll and Pecora showed that the subsystems $w$ and $w'$ will synchronize only if the sub-Lyapunov exponents are all negative. This theorem is only necessary, but not sufficient as it says nothing about the set of initial conditions which will allow for synchronization of $w$ and $w'$. In order to understand this theorem is it necessary to first understand subsystems. \cite{Theory}

Let an $n$ dimensional system be defined as the following

\begin{equation}
\dot{u} = f(u)
\end{equation}

We can divide the system in two parts arbitrarily. Let

\begin{equation}
v = [u_1, ..., u_m]^T
\end{equation}
\begin{equation}
w = [u_{m+1},...,u_n]^T
\end{equation}

and 

\begin{equation}
g = [f_1(u),...,f_m(u)]^T
\end{equation}
\begin{equation}
h = [f_{m+1}(u),...,f_n(u)]^T
\end{equation}

It's clear that

\begin{equation}
\dot{v} = g(v,w)
\end{equation}
\begin{equation}
\dot{w} = h(v,w)
\end{equation}

Now, we can create a new subsystem $w'$ identical to $w$ but use the solution $v$ instead of the variable $v'$. Intuitively, as the solution $v$ is used as an input for $w'$ it is often useful to think of $v$ driving the system $w'$.

\begin{equation}
\dot{v} = g(v,w)
\end{equation}
\begin{equation}
\dot{w} = h(v,w)
\end{equation}
\begin{equation}
\dot{w}' = h(v,w')
\end{equation}

Now lets look at the error between $w'$ and $w$, obviously synchronization will occur only if 

\begin{equation}
w'-w \rightarrow 0 \quad as \quad t\rightarrow \infty 
\end{equation}

After defining the subsystems $w'$ and $w$ we can understand Carroll and Pecora's theorem. Carroll and Pecora showed in their paper that the Lorenz system has two synchronous sub-systems. Recalling the form the Lorenz equations

\begin{equation}
\dot{x} = s(y-x)
\end{equation}
\begin{equation}
\dot{y} = rx - y - xz
\end{equation}
\begin{equation}
\dot{z} = xy - bz
\end{equation}

Consider these sub-systems

\begin{equation}
\dot{x}_1 = s(y-x_1)
\end{equation}
\begin{equation}
\dot{z}_1 = x_1y - bz_1
\end{equation}

and

\begin{equation}
\dot{y}_2 = rx - y_2 - xz_2
\end{equation}
\begin{equation}
\dot{z}_2 = xy_2 - bz_2
\end{equation}

We can show that sub-system 1 has negative Lyapunov exponents by examining the Jacobian. 

\begin{equation}
J = \left[ \begin{array}{ccc}
-s && 0\\
y && -b \end{array} \right]
\end{equation}

The characteristic polynomail is
\begin{equation}
(s+\lambda)(b+\lambda) = 0
\end{equation}

The roots are
\begin{equation}
\lambda_1 = -b
\end{equation}
\begin{equation}
\lambda_2 = -s
\end{equation}

Since $b$ and $s$ are positive, the origin is asymptotically stable and thus has negative Lyapunov exponents. While it is more complicated to show subsystem 2 has negative Lyapunov exponents, Carroll and Pecora used numerical techniques to find that for the system parameters $s = 10$, $r=28$ and $b=\frac{8}{3}$ the Lyapunov exponents for sub-system 1 and 2 are $(-1.81,-1.86)$ and $(-2.67, -9.99)$ respectively.

It would be desirable to have two full-sized system synchronize. In 1993 Kevin Cuomo and Alan Oppenhiem had the following idea: let $x(t)$ drive subsystem 2, then since $y_2 - y \rightarrow 0$ as $t\rightarrow \infty$ let $y_2$ drive subsystem 1. Using this idea we get the following full dimension system that should synchronize with the Lorenz with the same system parameters. \cite{Comm}

\begin{equation}
\dot{x}_s = s(y_s - x_s)
\end{equation}
\begin{equation}
\dot{y}_s = rx - y_s - xz_s
\end{equation}
\begin{equation}
\dot{z}_s = xy_s - bz_s
\end{equation}

Notice the solution $x$ from the Lorenz system is used as an input in the system where we would expect to see $x_s$ in the differential equations for $\dot{y}_s$ and $\dot{z}_s$. While this plan makes intuitive sense, we check the error dynamics of the Lorenz system and the synchronous system as defined above. 

\begin{equation}
e = [x \ \ y \ \ z]^T - [x_s \ \ y_s \ \ z_s]^T
\end{equation}

It is easy to show the error dynamics are as follows.

\begin{equation}
\dot{e}_1 = s(e_2 - e_1)
\end{equation}
\begin{equation}
\dot{e}_2 = -e_2 - xe_3
\end{equation}
\begin{equation}
\dot{e}_3 = xe_2 - be_3
\end{equation}

Using the following positive definite Lyapunov function we can check the stability of the origin.

\begin{equation}
V = \frac{1}{2} (\frac{1}{s}e_1^2 + e_2^2 + 4e_3^2)
\end{equation}

Taking the derivative of the Lyapunov function

\begin{equation}
\dot{V} = \frac{1}{s} e_1 \dot{e}_1 + e_2 \dot{e}_2 + 4 e_3\dot{e}_3
\end{equation}
\begin{equation}
\dot{V} = -(e_1 -\frac{1}{2}e_2)^2 - \frac{3}{4}e_2^2 - 4be_3^2
\end{equation}

we can conclude the origin is globally asymptotically stable, and thus the system $[x_s \ \ y_s \ \ z_s]^T$ will synchronize with the system $[x \ \ y \ \ z]^T$. Using $s = 10$, $r=28$ and $b=\frac{8}{3}$ the distance between the two systems is plotted in figure 4. The Lorenz system starts with initial conditions of $[0 1 0]$ while the synchronous system as defined in equation 27-29 have an initial conditions of $[1 2 3]$

\begin{figure}[H]
\centering
\includegraphics[width=0.5\textwidth]{plot4.png}
\caption{The distance between the two systems are plotted as a function of time}
\label{figure 3:}
\end{figure}

Figure 4 clearly shows how startling fast the systems synchronize even when there initial conditions are very far away. 

\section{Synchronous Choas Cryptogropher}

Kevin Cuomo and Alan Oppenhiem showed that it is possible to get two full dimensional chaotic systems to synchronize with each other by using the output from one of the systems to drive the other. Cuomo and Oppenhiem simulated this effect using circuits and showed the capability of the method to encrypt messages. \cite{Comm} Instead of using circuits, I wrote a simulation written in python to demonstrate the method.

Say you want to send your friend a song but you want to make sure that no one else can listen to the song. Tell your friend before hand the system parameters $s$, $r$ and $b$ making sure the values of the parameters create a chaotic system. The system parameters act as the key for the crypt.


Read your song into your program. Note that songs are merely just a list of numbers that describe the sound pressure as a function of time. For this demonstration, the classic "Call Me Maybe" by Carly Rae Jepsen is used. The waveform of the song is plotted below.

\begin{figure}[H]
\centering
\includegraphics[width=0.5\textwidth]{plot5.png}
\caption{Call Me Maybe" by Carly Rae Jepsen}
\label{figure 3:}
\end{figure}

Then, solve a Lorenz system with the parameters agreed upon earlier. Build the message $m(t)$ as 

\begin{equation}
m(t) = s(t) + x(t)
\end{equation}

where $x(t)$ is the $x$ solution of the Lorenz system and $s(t)$ is the song in which we want to encrypt. It is very important that $x(t)$ is much more powerful than $s(t)$. Since $x(t)$ is chaotic, the song is unrecognizable noise and thus safe for transit. 

Your friend then receives the message. To decrypt the message, your friend should solve the synchronous system

\begin{equation}
\dot{x}_s = s(y_s - x_s)
\end{equation}
\begin{equation}
\dot{y}_s = rm - y_s - mz_s
\end{equation}
\begin{equation}
\dot{z}_s = my_s - bz_s
\end{equation}

Since the systems are synchronous, $x_s \rightarrow x$. Thus to decrypt the message

\begin{equation}
s(t) \approx m(t) - x_s(t)
\end{equation} 

Figure 6 shows the decrypted song compared to the actual song. While some information is lost due to the encryption and decryption, it is clear that the method works. Playing the decrypted song, there is no noticeable difference between the two versions.

\begin{figure}[H]
\centering
\includegraphics[width=0.5\textwidth]{plot6.png}
\caption{The full song (blue) and decyrpted song (green) are shown.}
\label{figure 3:}
\end{figure}

A natural question to ask is how sensitive is synchronization to the system parameters. In figure 7, the system parameters are changed by 30\%. The figure shows that the systems did not synchronize, and playing the songs confirms the song is unrecognizable. Changing the system parameters to only 10\% does not change the figure significantly, but the song becomes barely recognizable. 

\begin{figure}[H]
\centering
\includegraphics[width=0.5\textwidth]{plot7.png}
\caption{The full song (blue) and decyrpted song (green) are shown with parameters differing 30\%}
\label{figure 3:}
\end{figure}

The theory and method of using chaos synchronization as described by Kevin Cuomo and Alan Oppenhiem to encrypt data is thus confirmed. 



\begin{thebibliography}{5}


\bibitem{Theory} Carroll, Thomas L., and Louis M. Pecora. "Synchronizing chaotic circuits." Circuits and Systems, IEEE Transactions on 38.4 (1991): 453-456.

\bibitem{Comm} Cuomo, Kevin M., and Alan V. Oppenheim. "Circuit implementation of synchronized chaos with applications to communications." Physical review letters 71.1 (1993): 65-68.

\bibitem{Exp} Cvitanovic, Predrag, et al. "Chaos: Classical and Quantum (Niels Bohr Institute, Copenhagen, 2008)." ChaosBook. org.



\end{thebibliography}




\end{document}



