hierarchical-clustering-java
============================

Implementation of an agglomerative hierarchical clustering algorithm in Java. Different linkage approaches are supported:
* Average Linkage
* Single Linkage
* Complete Linkage

What you put in
---------------

Pass an distance matrix and a cluster name array along with an linkage strategy to the clustering algorithm:

    String[] names = new String[] { "O1", "O2", "O3", "O4", "O5", "O6" };
    double[][] distances = new double[][] { 
        { 0, 1, 9, 7, 11, 14 },
        { 1, 0, 4, 3, 8, 10 }, 
        { 9, 4, 0, 9, 2, 8 },
        { 7, 3, 9, 0, 6, 13 }, 
        { 11, 8, 2, 6, 0, 10 },
        { 14, 10, 8, 13, 10, 0 }};

    ClusteringAlgorithm alg = new DefaultClusteringAlgorithm();
    Cluster cluster = alg.performClustering(distances, names,
        new AverageLinkageStrategy());

Alternatively, you can pass a [pdist](http://www.mathworks.com/help/stats/pdist.html)-like matrix containing one row:

    String[] names = new String[] { "O1", "O2", "O3", "O4", "O5", "O6" };
    double[][] pdist = new double[][] {
				{1, 9, 7, 11 ,14 ,4 ,3 ,8 ,10 ,9 ,2 ,8 ,6 ,13 ,10}
		};
    ClusteringAlgorithm alg = new PDistClusteringAlgorithm();
    Cluster cluster = alg.performClustering(pdist, names, new AverageLinkageStrategy());

What you get out
----------------

The algorithm creates a *Cluster* instance representing an hierachy of clusters based on their distances.
You may want to visualize the result using the Swing component *DendrogramPanel*:

    DendrogramPanel dp = new DendrogramPanel();
    dp.setModel(cluster);

When embedded into a JFrame the dendrogram panel should display this:

![Screenshot](https://raw.github.com/lbehnke/hierarchical-clustering-java/master/etc/screenshot1.png "Average linkage")

Same data but different linkage strategy (MinimumLinkageStrategy) result in a slightly different diagram:

![Screenshot](https://raw.github.com/lbehnke/hierarchical-clustering-java/master/etc/screenshot2.png "Minimum linkage")

Wikipedia references
--------------------
* [Average linkage clustering](http://en.wikipedia.org/wiki/UPGMA "Average linkage clustering")
* [Single linkage clustering](http://en.wikipedia.org/wiki/Single-linkage_clustering "Single linkage clustering")
* [Complete linkage clustering](http://en.wikipedia.org/wiki/Complete_linkage_clustering "Complete linkage clustering")

License
-------
Licensed under the Apache License, Version 2.0 (the "License"); 
you may not use this file except in compliance with the License. 
You may obtain a copy of the License at (http://www.apache.org/licenses/LICENSE-2.0).
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, 
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. 
See the License for the specific language governing permissions and limitations under the License.
