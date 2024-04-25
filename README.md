# ParPy
ParPy is a python based script that measures the parallelism of replicate samples in multivariate space. Intended application is here: [doi]
### Inspired by: 
[Junya Watanabe, 2022](https://onlinelibrary.wiley.com/doi/full/10.1002/ece3.9674#ece39674-bib-0071) & [Härer & Rennison, 2022](https://onlinelibrary.wiley.com/doi/full/10.1002/ece3.9674#ece39674-bib-0071)
## Step-by-step Code Breakdown:
1) $\[
\cosΘ = r = \frac{u \cdot v}{\|u\| \cdot \|v\|}
\]$ - Where a list of vector elements for $v = Replicate_1$ and $u = Replicate_2$ are calculated by 
  $\[
\binom{n}{2} = \frac{n \cdot (n-1)}{2}
\]$
And all vector elements are filled by their pairwise PC eigenvector value $\ x_i = PC_n , y_i = PC_{n+1}\$ then fitted into a N dimension tupple $\{ [(x_1, y_1), (x_2, y_2), \ldots, (x_i, y_i)] \}$

2) Magnitudes of $\|u\|$ and $\|v\|$ are calculated by taking the euclidean distance of the respective vector ($\|u\|$ or $\|v\|$) from origin (0,0). Which allows us the ability to calculate distance of a single point in a 2D space, thus giving us the ability to analyze the angles between replicates.

**Explanation:** The ability to calculate angle between points requires more than 1 vector coordinate. But when the function to analyze parallelism of replicates across space arises, you only have a single point in space. To compound the issue, PC eigenvalues are dimensionaly reduced value interactions between your data points, thus it isn't possible to mix and match different axises of PC space since you aren't able to interpret what each axis and value represents. With the above script, to avoid both issues we do the following; We create a second point at origin so that we can calculate distances and angles for each one of our points, and we create every possible PC pairwise combination of points for each of the samples, so that we are not comparing and making inferences off of different PC axis interactions. **This does however create a problem, a large number of angles for each sample, so how do we coalesce everything to a single interpretable integer?**  

