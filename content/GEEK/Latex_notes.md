
+++
date = "2017-08-02T16:24:01+08:00"
title = "Latex Notes"
+++
# Add a forced line break inside a table cell
```
\begin{tabular}{|c|c|c|}
\hline
Foo bar & \begin{tabular}[x]{@{}c@{}}Foo\\bar\end{tabular} & Foo bar \\
\hline
\end{tabular}
```
where x is either t, c, or b to force the desired vertical alignment.

In case this is needed in more than a couple of places, it's better to define a command

```
\newcommand{\specialcell}[2][c]{%
  \begin{tabular}[#1]{@{}c@{}}#2\end{tabular}}
```
so the table line before can be one of
```
Foo bar & \specialcell{Foo\\bar} & Foo bar \\    % vertically centered
Foo bar & \specialcell[t]{Foo\\bar} & Foo bar \\ % aligned with top rule
Foo bar & \specialcell[b]{Foo\\bar} & Foo bar \\ % aligned with bottom rule
```
Notice the @{} to suppress added space before and after the cell text.

# Add multiple equations and number them
```latex
\begin{subequations}\label{eq:litdiff}
  \begin{align}
    \rho v^2_p(\theta) &= \frac{1}{2} [ C_{33} + C_{44} + (C_{11} - C_{33})sin^2 \theta + D(\theta) ]
    \label{eq:velocity_P_wave}\\
    \rho v^2_{SV}(\theta) &= \frac{1}{2} [ C_{33} + C_{44} + (C_{11} - C_{33})sin^2 \theta - D(\theta) ]
    \label{eq:velocity_SV}\\
    \rho v^2_{SH}(\theta) &= C_{66}sin^2(\theta) + C_{44}cos^2 \theta
    \label{eq:velocity_SH}
  \end{align}
\end{subequations}
```

# Add matrix
```
\begin{bmatrix}    
  C_{11} & (C_{11}-2C_{66}) & C_{13} & 0 & 0 & 0\\
  (C_{11}-2C_{66}) &  C_{11} & C_{13} & 0 & 0 & 0 \\
  C_{13} & C_{13} & C_{33} & 0 & 0 & 0 \\
  0 & 0 & 0 & C_{44} & 0  & 0 \\
  0 & 0 & 0 & 0 & C_{44} & 0 \\
  0 & 0 & 0 & 0 & 0 & C_{66} \\
\end{bmatrix}
```
```
\documentclass{article}
\usepackage{amsmath}

\begin{document}

\[
A =
  \begin{matrix}\begin{pmatrix}x & y\end{pmatrix}\\\mbox{}\end{matrix}
  \begin{pmatrix} a & b \\ c & d \end{pmatrix}
  \begin{pmatrix} x \\ y \end{pmatrix}
\]

\end{document}
```
# Latex font
```

\tiny
\scriptsize
\footnotesize
\small
\normalsize
\large
\Large
\LARGE
\huge
\Huge
```
