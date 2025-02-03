# Cross-reactivity breadth for influenza A viruses

Data and R scripts were used to support the paper: 
Bingyi Yang*, Katelyn M. Gostic, Dillon C. Adam, Ru Zhang, Tal Einav, Liping Peng, Sook San Wong, Tim K. Tsang, Derek A. T. Cummings, Sheena G. Sullivan, Sarah Cobey, Benjamin J. Cowling. Intrinsic patterns of influenza A antibody cross-reactivity and implications for antibody landscapes. 2024.

Correspondance regarding this study should be addressed to Bingyi Yang (byyang@connect.hku.hk).

The primary analyses were conducted using the markdown file [main_analysis.Rmd](https://github.com/byyangyby/influenza_A_cross-reactivity/blob/main/main_analysis.Rmd), which generates the main figures presented in the manuscript.

## Analysis software and packages
This project uses the following R packages: ``tidyverse``, ``readxl``, ``openxlsx``, ``ggsci``, ``lubridate``, ``ggpubr``, ``brms``, ``rstan``, ``colorspace``, ``posterior``, ``pROC``, ``ggthemes``, ``truncnorm``, ``tableone``, ``fdrtool``, and ``patchwork``.

## Data sources
All data for the analysis were sourced from previously published studies or public reports. We processed the data to facilitate our analysis, primarily by transforming the differences in isolation years between immunizing and tested viruses. Specifically, data were sourced from the following studies grouped by different host.
1. Ferrets
   - The Francis Crick Institute Worldwide Influenza Centre lab [Annual and interim reports](https://www.crick.ac.uk/research/platforms-and-facilities/worldwide-influenza-centre/annual-and-interim-reports), 2003-2022.
   - Smith, D. J. et al. [Mapping the antigenic and genetic evolution of influenza virus.](https://www.science.org/doi/10.1126/science.1097211) Science 305, 371-376 (2004).
   - Fonville, J. M. et al. [Antibody landscapes after influenza virus infection or vaccination.](https://www.science.org/doi/10.1126/science.1256427) Science 346, 996-1000 (2014).
   - Fonville, J. M. et al. [Antigenic Maps of Influenza A(H3N2) Produced With Human Antisera Obtained After Primary Infection.](https://academic.oup.com/jid/article/213/1/31/2459222) J Infect Dis 213, 31-38, (2016).

2. Human, 9-24 months
   - Fonville, J. M. et al. [Antigenic Maps of Influenza A(H3N2) Produced With Human Antisera Obtained After Primary Infection.](https://academic.oup.com/jid/article/213/1/31/2459222) J Infect Dis 213, 31-38, (2016).

3. Human, all ages
   - Fonville, J. M. et al. [Antibody landscapes after influenza virus infection or vaccination.](https://www.science.org/doi/10.1126/science.1256427) Science 346, 996-1000 (2014).
   - Hinojosa, M. et al. [Impact of Immune Priming, Vaccination, and Infection on Influenza A(H3N2) Antibody Landscapes in Children.](https://academic.oup.com/jid/article/224/3/469/5934948) J Infect Dis 224, 469-480 (2021).
   - Ertesvag, N. U. et al. [Seasonal influenza vaccination expands hemagglutinin-specific antibody breadth to older and future A/H3N2 viruses.](https://www.nature.com/articles/s41541-022-00490-0) NPJ Vaccines 7, 67 (2022).
   - Yang, B. et al. [Life course exposures continually shape antibody profiles and risk of seroconversion to influenza.](https://journals.plos.org/plospathogens/article?id=10.1371/journal.ppat.1008635) PLoS Pathog 16, e1008635 (2020).
   - Lessler, J. et al. [Evidence for antigenic seniority in influenza A (H3N2) antibody responses in southern China.](https://journals.plos.org/plospathogens/article?id=10.1371/journal.ppat.1002802) PLoS Pathog 8, e1002802 (2012).

Table. Data sources used in the study.

| Data source          | Host             | Subtype                           | Strains   | Antibody  | Age group    | Year of Birth | Sample size | Year of sampling                                                 | Antisera type           | Exposure                          |
|---------|------|------|------|------|------|------|------|------|------|------|
| Crick's report       | Ferret           | H1N1; H3N2                        | 1999-2022 | HAI; nAbs | \--          | \--           | \--         | \--                                                              | Primary                 | Infection                          |    
| Smith et al. 2004    | Ferret           | H3N2                              | 1968-2004 | HAI       | \--          | \--           | \--         | \--                                                              | Primary                 | Infection                          |
| Fonville et al. 2014 | Ferret           | H3N2                              | 1968-2012 | HAI       | \--          | \--           | \--         | \--                                                              | Primary                 | Infection                          |
| Fonville et al. 2016 | Ferret           | H3N2                              | 1989-2011 | HAI       | \--          | \--           | \--         | \--                                                              | Primary                 | Infection                          |
| Fonville et al. 2016 | Human - Children | H3N2                              | 1989-2011 | HAI       | 9-24 months  | \--           | 5           | 1995, 2000, 2004                                                 | Likely primary          | PCR-confirmed H3N2 infections      |                                              
| Fonville et al. 2014 | Human            | H3N2                              | 1968-2012 | HAI       | 2-90 years   | 1917-2005     | 69          | 2007, 2008, 2009, 2010, 2011, 2012                               | Secondary               | Infected/vaccinated                |
| Hinojosa et al., 2021| Human            | H3N2                              | 1968-2013 | HAI       | 7-18 years   | 1998-2009     | 72          | 2016                                                             | Secondary               | Vaccinated                         |
| Ertesvag et al., 2022| Human            | H3N2                              | 1968-2014 | HAI       | 2-18 years   | 1995-2011     | 42          | 2013, 2014                                                       | Secondary               | Vaccinated                         |
| Yang et al., 2020    | Human            | H3N2                              | 1968-2014 | HAI       | 2-86 years   | 1924-2008     | 777         | 2010, 2014                                                       | Secondary               | Not available                      |                   
| Lessler et al. 2012  | Human            | H3N2                              | 1968-2008 | nAbs      | 7-81 years   | 1928-2002     | 191         | 2009                                                             | Secondary               | Not available                      |                    
