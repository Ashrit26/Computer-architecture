# K-Means Clustering Algorithm

Implementation of k means algorithm using the CUDA architecture

## By

* Ishaan R Dharamdas (16CO117)
* M R Ashrit (16CO122)

---
To run:
  * The Makefile will produce executables
     o "omp_main" for OpenMP version
     o "mpi_main" for MPI version
     o "cuda_main" for CUDA version
     o "seq_main" for sequential version

  * The list of available command-line arguments can be obtained by
    running -h option
     o For example, running command "omp_main -h" will produce:
       Usage: main [switches] -i filename -n num_clusters
             -i filename    : file containing data to be clustered
             -b             : input file is in binary format (default no)
             -n num_clusters: number of clusters (K must > 1)
             -t threshold   : threshold value (default 0.0010)
             -p nproc       : number of threads (default system allocated)
             -a             : perform atomic OpenMP pragma (default no)
             -o             : output timing results (default no)
             -d             : enable debug mode

Input file format:
The executables read an input file that stores the data points to be 
clustered. A few example files are provided in the sub-directory 
./Image_data. The input files can be in two formats: ASCII text and raw 
binary.

  * ASCII text format:
    o Each line contains the coordinates of a single data point
    o The number of coordinates must be equal for all data points
  * Raw binary format:
    o There is a header of 2 integers.
    o The first 4-byte integer must be the number of data points.
    o The second integer must be the number of coordinates.
    o The rest of the file contains the coordinates of all data 
      points and each coordinate is of type 4-byte float.

Output files: There are two output files:
  * Coordinates of cluster centers
    o The file name is the input file name appended with ".cluster_centres".
    o It is in ASCII text format.
    o Each line contains an integer indicating the cluster id and the
      coordinates of the cluster center.
  * Membership of all data points to the clusters
    o The file name is the input file name appended with ".membership".
    o It is in ASCII text format.
    o Each line contains two integers: data point index (from 0 to 
      the number of points) and the cluster id indicating the membership of
      the point.