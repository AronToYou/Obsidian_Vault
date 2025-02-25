# Technology in NavVis
## MLX
- SLAM software
	- augmented by Visual Odometry
- Geo-registration
	- Compatible with Control Points used by
		- Total Stations
		- GNSS rovers
## Ivion Processing


# External Sources
slam_toolbox
- Data points called PosedScan objects consist of
	- pose (using odometry)
	- laser scan (LiDAR)
- A queue of PosedScans which are processed by the algorithm
	- constructing a pose graph, from which
		- odometry refined using laser scan matching
		- pose calculated
		- loop closures are discovered
- Odometry
	- Estimation of movement by data from 
		- actuators
		- consecutive camera images
- Point-set registration
	- finding spatial-transformations which align 2 point clouds
- Solvers
	- Ceres (only working one)
	- G2O
	- SPA
	- GTSAM

Ceres Solver
- Non-linear Least Squares
	- bounds constrained
	- [[clausing2004.pdf|robustified]]
	- automatic differentiation
		- Every computer calculation is a sequence of differentiable arithmetic operations
- General Unconstrained Minimization

Julia
- prototyping
- JuMP, NLPModels
- Non-linear Least Squares [NLLSsolver](https://github.com/ojwoodford/NLLSsolver.jl)

[[ISTQB_CTFL_Syllabus-v4.0.pdf|ISTQB Certification]]