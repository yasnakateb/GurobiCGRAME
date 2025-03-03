# Integrating Gurobi with CGRA-ME

The **CGRA-ME** framework enables modeling, simulation, and optimization of **Coarse-Grained Reconfigurable Arrays (CGRAs)** for high-performance applications such as **signal processing** and **machine learning**. It provides flexibility in exploring different configurations to balance factors like power consumption, throughput, and scheduling. **Gurobi**, a powerful mathematical optimization solver, can be integrated with CGRA-ME to solve complex problems like task scheduling and resource allocation. 

This guide will walk you through setting up Gurobi within CGRA-ME to optimize CGRA designs, enhancing performance and resource efficiency.

---

## Step-by-Step Guide

### 1. Download and Install CGRA-ME
- Download CGRA-ME from the official site:  
  👉 [CGRA-ME Download](https://cgra-me.ece.utoronto.ca/download/)  

### 2. Download Gurobi
- Get the appropriate **Gurobi tar file** for your operating system:  
  👉 [Gurobi Downloads](https://www.gurobi.com/downloads/gurobi-software/)  
- This guide assumes **Ubuntu** as the target system.

### 3. Extract the Gurobi Package  

    tar -xvf gurobi<version>.tar.gz


### 4. Obtain a Free Gurobi License  
- If you have an institutional email, you can get a **Named-User Academic License** from Gurobi.  
- **Note**: The license key may expire after one day.

### 5. Organize Directory Structure  
- Make sure **CGRA-ME** and **Gurobi** share the same parent directory to ensure smooth setup and integration:
  
        📂 Parent_Directory/  
             ├── 📂 CGRA-ME/  
             │   ├── src/  
             │   ├── bin/  
             │   ├── examples/  
             │   └── Makefile  
             ├── 📂 gurobi702/  
             │   ├── bin/  
             │   ├── lib/  
             │   ├── doc/  
             │   └── license/  

### 6. Activate Gurobi

Navigate to the bin subdirectory of the extracted Gurobi folder. Run the following command to activate Gurobi with your license key:

    ./grbgetkey <your-license-key>


### 7. Configure Environment Variables

Open your .bashrc file and add the following lines to set the Gurobi environment:

    export GUROBI_HOME="$HOME/gurobi[your_version]"
    export PATH="${PATH}:${GUROBI_HOME}/bin"
    export LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:${GUROBI_HOME}/lib"

Replace [your_version] with the specific version of Gurobi you're using. Save and apply the changes:

    source ~/.bashrc

### 8. Compile CGRA-ME with Gurobi

Navigate to the CGRA-ME directory and run:

    make

If you encounter an error about Gurobi not found, check and update the paths in .bashrc.

### 9. (Optional) Using CGRA-ME with Docker

If you are running CGRA-ME inside a Docker container, remember to commit and push your changes to avoid losing them:

    docker commit <container_id> <image_name>
    docker push <image_name>


## 🎉 Congratulations!

You have successfully integrated Gurobi with CGRA-ME. You can now take advantage of Gurobi's optimization strength to boost CGRA design efficiency! 
