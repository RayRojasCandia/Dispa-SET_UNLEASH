<div style="display: flex; justify-content: center">
  <img src="https://github.com/user-attachments/assets/7e6106c2-eeef-4ce7-a9ff-707f6499c704" width="200" height="150" style="margin-right: 10px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/a8d1c34a-f5c1-4ab9-99c3-0d965ab5a676" width="310" height="124">
</div>

<h1>
  Dispa - SET UNLEASH
  <br>
  Data Framework and EWH/HPWH-based VPP Integration for Belgian Flexibility Assessment
</h1>

Ray Rojas<sup>1,2</sup>, David Rojas<sup>1</sup>, Marco Navia<sup>1</sup>, Julio Pascual<sup>2</sup>, Sylvain Quoilin<sup>1</sup>
<br>
> <sup>1</sup>University of Liège, Department of Aerospace and Mechanical Engineering, Sart Tilman, Liège, Belgium
> <br>
> <sup>2</sup>Public University of Navarre, Department of Electrical, Electronic and Communication Engineering, Pamplona, Spain

### Overview 

This repository accompanies the UNLEASH project deliverables (D5.1 and D5.2), providing:
- Automated data pipelines for the Dispa-SET Unit Commitment and Economic Dispatch (UCED) model, covering 30 European countries (2016–2023) at hourly/30-min/15-min resolution.
- Virtual Power Plant (VPP) modeling of 500,000 residential water heaters (1245 MW capacity, 7543 MWh storage) as a Boundary Sector in Dispa-SET.

### Key Features  
- **Open-Source Data Framework**  
  - Standardized data processing for Dispa-SET via Python/API automation (ENTSO-E, web scraping).  
  - Covers techno-economic (e.g., plant efficiencies, costs) and dynamic (e.g., hourly demand, VRES generation) inputs.  
- **VPP as Boundary Sector**  
  - Models aggregated water heaters as a P2X technology with thermal storage constraints.  
  - Includes SOC dynamics and demand profiles.
 
### Getting Started
1. Install **Dispa-SET-Masters** (base framework) following the **Quick start** section steps from:<br>
https://github.com/energy-modelling-toolkit/Dispa-SET/tree/master

2. Clone **UNLEASH** repository
```bash
git clone https://github.com/RayRojasCandia/Dispa-SET_UNLEASH.git
cd Dispa-SET_Unleash/scripts
python build_and_run_Boundary_Sector_UNLEASH.py
python read_results_Boundary_Sector_UNLEASH.py
```

### Configuration  
The simulation is pre-configured with the **(2)_BE-NUC** scenario (Isolated Belgian System with nuclear units at 2023) in the Configuration file:  
```bash
ConfigFiles/Config_BE_Boundary_Sector.xlsx
```
To run additional scenarios, configure the settings in the ConfigFile according to the [Dispa-SET documentation](https://www.dispaset.eu/en/latest/implementation.html). This will ensure the model is set up for your specific use case.

### Key Results  
- **Curtailment Reduction**: VPP decreases renewable curtailment by 6.7–79.4% depending on VRES penetration.  
- **Congestion Management**: Reduces fully loaded hours on critical interconnections (BE-FR, BE-DE) by 5–8%.  
- **Load Shifting**: Achieves 1.75 TWh/year of flexible demand, lowering shifted load by 2–5% across scenarios.  

### Citation  
If using this repository, please cite the accompanying paper:

##### APA (7th Edition)  
```plaintext
Rojas, R., Tareen, U., Rojas, D., Navia, M., Pascual, J., & Quoilin, S. (2025). 
Enhancing grid flexibility with virtual power plants: A study on the integration 
of residential water heaters and heat pumps in the Belgian power system. 
In Proceedings of the 38th International Conference on Efficiency, Cost, 
Optimization, Simulation and Environmental Impact of Energy Systems (ECOS 2025). 
Paris, France. UNLEASH Project.
```

##### BibTeX (For LaTeX Users)  
```bibtex
@inproceedings{RojasEtAl2025,
  title     = {Enhancing Grid Flexibility with Virtual Power Plants: 
               A Study on the Integration of Residential Water Heaters 
               and Heat Pumps in the Belgian Power System},
  author    = {Rojas, Ray and Tareen, Umair and Rojas, David and 
               Navia, Marco and Pascual, Julio and Quoilin, Sylvain},
  booktitle = {Proceedings of the 38th International Conference on 
               Efficiency, Cost, Optimization, Simulation and 
               Environmental Impact of Energy Systems (ECOS 2025)},
  year      = {2025},
  address   = {Paris, France},
  note      = {UNLEASH Project (Unlocking Residential Demand Flexibility)}
}
```  

### Contributing  
Contributions are welcome! submit a Pull Request for:  
- Additional data sources (e.g., newer ENTSO-E datasets).  .  
- Scenario extensions (other European regions, hybrid storage).  

### License  
Dispa-SET is a free software licensed under the “European Union Public Licence" EUPL v1.2. It can be redistributed and/or modified under the terms of this license.  

### Contact
for Dispa-SET integration support
- [rarcandia@uliege.be](mailto:rarcandia@uliege.be).
- [squoilin@uliege.be](mailto:squoilin@uliege.be) 
