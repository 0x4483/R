## Network with R using `ggplot2` and `igraph`

### Step 1: obtain adjacent matrix
airport_adj <- get.adjacency(graph.edgelist(as.matrix(df),
                                            directed=TRUE))

### Step 2: convert into igraph object
airport_graph <- graph_from_adjacency_matrix(airport_adj)


### Step 3: graph using geom_edges and geom_nodetext

ggplot(air_data, 
       aes(x, y, xend = xend, yend = yend)) +
  geom_edges(arrow = arrow(length = unit(0.3, "lines")), 
             aes(color = as.factor(...)), alpha = 0.5) +
  geom_nodetext(aes(label = vertex.names, size = degree * 1.5), 
                color = "blue", fontface = "bold")
