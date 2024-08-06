# Paper

- **Title**: CoMPosT: Characterizing and Evaluating Caricature in LLM Simulations
- **Authors**: Myra Cheng, Tiziano Piccardi, Diyi Yang
- **Link**: http://arxiv.org/abs/2310.11501
- **Tags**: Bias, Stereotype, Personas simulations
- **Year**: 2024
  
# Summary

## What?

1. New evaluation **framework** to measure open-ended LLM simulations’ susceptibility to caricature:
    - **C**ontext : Where and when does the simulated scenario occur?
    - **M**odel : What LLM is used?
    - **P**ersona : Whose opinion/action is simulated?
    - **T**opic : What is the simulation about?

2. New evaluation **metric** for caricature in LLM outputs (=emphasis on persona instead of topic)

3. Experimental **evaluation** of various LLM simulations with framework and metric:
    - Contexts :
      - Online forum (C1)
      - Interview (C2)
    - Model : GPT-4 
    - Personas : 
      - Age: 20-year-old person, 40-year-old person, 80-year-old person
      - Political ideology: conservative person, liberal person, moderate person
      - Race/ethnicities: Asian person, Black person, Hispanic person, Middle-Eastern person, white person
      - Gender: man, non-binary person, woman
    - Topics :
      - C1 : varying specificity levels (scale 1-5) and controversy levels (from Wikihow to ProCon.org)
      - C2 : sample from most contentious questions from Pew Research’s American Trends Panel OpinionQA


## Context

- Persona simulations with LLMs increasingly used in social science experiments/public opinion surveys/education/product design/psychology/healthcare/skill training/law.
- Lack of evaluation methods that apply to open ended settings and go beyond believability of these simulations.
- Related work :
  - hbh
  - hb 

## Method

*For reference, S(p,t,c) is a simulation for context c, persona p and topic t*

Caricature evaluation :
  - Individuation : Binary classifier used to differentiate S(p,t,c) from S(_,t_c). A persona is individuated if the classifier has high accuracy.
  - Exaggeration : Contextualized semantic axes method (Lucy et al, 2022) applied to persona-topic axes and using Fighting Words method (Monroe et al., 2008) to construct set of seed words for p and for t. A persona is exaggerated if its associated simulations are more related to the persona than the topic.
  
## Results

- Political and marginalized groups highly susceptible to caricature.
- General and uncontroversial topics highly susceptible to caricature.

## Limitations
- Non systematic and comprehensive metric : potential false positives + non-detected biases/stereotypes ≠ from caricature
- Language dimension not included in framework + not tested
- Topics tested very US-centered
- Missing marginalized groups in personas (intersection, LGBT, Muslims, Jewish, non western countries)

## Questions

* Most topics selected would naturally vary across social cultures : is metric really a good measure of caricature? (could some variations labelled as caricature sometimes be simply logical/"normal"?)
* How to evaluate stereotype beyond just caricature, which is not really a perfect proxy?
* What potential applications are meant to be covered by contexts and topics selected?
* What other contexts/topics would it be interesting to test for?
* How do you ensure robustness of such an experiment especially along the persona axis? I wonder if models are aligned to "protect" certain known demographic groups under certain known labels (like black) and could potentially do much worse when simulating for personas from other groups (minorities outside the US for example) and/or personas from the same group but under a different label (afronegro)? Rates of caricature for non-binary points towards this possibility.
