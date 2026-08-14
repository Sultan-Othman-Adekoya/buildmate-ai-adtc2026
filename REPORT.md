# Technical Report — [BuildMate AI: Offline Civil Engineering Inspection Assistant]

**Team ID:** your-team-id  
**Domain:** Corporate / Enterprise 
**Model:** Phi-3-mini-4k-instruct-Q4_K_M

---

## Problem

BuildMate AI is an offline AI-powered inspection assistant designed for civil engineers, site inspectors, construction supervisors, and infrastructure agencies operating in environments with unreliable or unavailable internet connectivity.

Construction sites frequently require engineers to document observations, analyse structural conditions, prepare inspection reports, and recommend corrective actions. Existing AI assistants typically rely on cloud-based APIs, making them unsuitable for remote projects, military infrastructure, mining operations, disaster response, and many regions across Africa where connectivity is intermittent.

BuildMate AI enables engineers to generate professional inspection reports, concrete pour reports, daily site reports, and engineering recommendations entirely on-device without transmitting sensitive project information to external servers.

Running the model locally provides several advantages:

Complete offline operation
Protection of confidential engineering and government infrastructure data
Low operating cost (no API fees)
Fast response times without network latency
Deployment on standard consumer laptops used in the field

---

## Design Decisions

Base Model

Microsoft Phi-3 Mini 4K Instruct

Phi-3 Mini was selected because it provides strong reasoning and instruction-following performance while remaining small enough to execute efficiently on commodity hardware.

Quantization

GGUF Q4_K_M

The Q4_K_M quantization was selected because it offers an excellent balance between:

Memory usage
Inference speed
Engineering report quality

while remaining comfortably within the 8 GB RAM constraint.

Alternatives Considered

Q8_0

Higher output quality
Memory usage approached or exceeded the target hardware limits
Slower inference

Q2_K

Lower memory footprint
Noticeable reduction in engineering terminology accuracy
Less reliable structured report generation

Q4_K_M provided the best overall trade-off.

---

## Constraints

Target hardware: consumer laptop with 8 GB RAM
CPU-only inference using llama.cpp
No dedicated GPU or NPU acceleration required
Ubuntu 22.04 compatible
Windows 11 development environment
Designed to function with zero internet connectivity after installation
Suitable for construction sites, rural infrastructure projects, disaster recovery operations, and secure engineering environments

---

## Benchmarks

| Metric              | Value                                                |
| ------------------- | ---------------------------------------------------- |
| Machine             | HP Laptop (Intel processor, Windows 11)              |
| RAM at peak         | ~3.5–4.0 GB *(expected)*                             |
| Time to first token | To be measured                                       |
| Generation speed    | To be measured                                       |
| Thermal throttling  | None observed during normal testing *(if confirmed)* |
