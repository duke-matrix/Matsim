# MATSim Lagos Traffic Simulation

## Project Overview
A comprehensive traffic simulation for Lagos, Nigeria using MATSim 13.0, implementing the hyper-dense compression specification pattern:

```
JMS.Lagos:OSM→N|Pop{hwms}+M{cbw}|T[BRT,df]|cfg|out{t,ms,σ}+V|13|M⁷
```

## Compression Spec Mapping

| Symbol | Component | Implementation | Description |
|--------|-----------|----------------|-------------|
| **Ω** | OSM→Network | `NetworkBuilder.java` | Converts OpenStreetMap data to MATSim network |
| **Δ** | Population{hwms} | `PopulationBuilder.java` | Generates agents with home→work→market→school activities |
| **M** | Modes{cbw} | Multiple classes | Car, Bus (PT), Walk transport modes |
| **τ** | Transit[BRT,df] | `TransitBuilder.java` | BRT lines + Danfo (informal transit) routes |
| **C** | Configuration | `SimulationRunner.java` | MATSim config with iterations and parameters |
| **Σ** | Output{t,ms,σ} | `ResultsAnalyzer.java` | Travel times, modal split, agent scores |
| **ν** | Visualization | `ResultsAnalyzer.java` | Summary reports and statistics |
| **13** | Version | `pom.xml` | MATSim 13.0 |
| **M⁷** | Modular | 7 classes | Clean modular architecture |

## Quick Start

```bash
# Build the project
cd matsim-lagos-app
mvn clean package

# Run simulation
java -jar target/matsim-lagos-app-1.0.0-jar-with-dependencies.jar
```

## Lagos-Specific Features

### Transit System
- **BRT Lines**: CMS-Mile2, Oshodi-Victoria Island
- **Danfo Routes**: Yaba-Surulere, Ikeja-Agege, Apapa-Marina

### Traffic Patterns
- Morning Peak (7-10 AM): 2.5x congestion
- Evening Peak (5-8 PM): 2.8x congestion
- Midday: 1.5x congestion

### Agent Activities
```
Home → Work → [Market] → [School] → Home
```

## Output Analysis
Results written to `output/lagos-simulation/` including:
- Modal split statistics
- Travel time analysis
- Agent score evaluation
- Summary report generation

---
*Compression: JMS.LG:Ω→{ΔA[4],τ[5],C²}→Σ+|13M⁷*