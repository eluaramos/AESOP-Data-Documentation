Health data
=====

Primary Health Care (PHC)
--------------------------------

Description
^^^^^^^^^^^

Primary Healthcare Encounters (PHCE) have been used in many countries as early warning and sentinel surveillance of disease outbreaks.

Data of PHCE for Brazil were extracted from the national information system for primary healthcare (SISAB) maintained by the Ministry of  Health (MoH). SISAB is a decentralized system; every Brazilian city runs a local version of it, sending monthly automated reports to the MoH. Since 2016, its use has become mandatory for receiving federal funds for PHC. As of today, 12 million PHCE are being reported monthly. 

Reporting to SISAB requires classifying the Reason for Encounter (REF) using the International Classification of Disease 10th edition (ICD-10) or the International Classification of Primary Care (ICPC-2).

We included a broad set of symptoms, syndromes, and diagnostics possibly related to influenza or COVID-19 in the Upper Respiratory Infection (URI) group in order to develop a warning system with high sensitivity.

ICPC codes used are on the table below. ICD-10 codes to the same concepts were mapped to ICPC-2 .

===  ====================
A03  Fever
R05  Cough
R07  Sneeze
R08  Other respiratory symptoms
R74  Upper Respiratory Infection
R76  Amigdalitis
R77  Laringitis
R80  Influenza
R83  Other respiratory infections
===  ====================

Data access information
^^^^^^^^^^^^^^^^^^^^^^^

Data is open access in the MoH websites, particularly on the following sites: 

- https://sisaps.saude.gov.br/painelsaps/
- https://sisab.saude.gov.br/

Methods of data collection
^^^^^^^^^^^^^^^^^^^^^^^^^^

Data is collected on the report generation systems in the above-mentioned websites. We developed web-scrapping bots to collect the data we are interested in.

Data is updated monthly by the Ministry of Health and we are also harvesting it on monthly basis. Beginning in 2023 we will harvest the data on weekly basis. 

Data-specific information
^^^^^^^^^^^^^^^^^^^^^^^^^

Data is one dataset where each line is corresponds to one Brazilian city in one month of the studied period. The variables are city population, location, number of PHC teams and facilities and the number of PHCE in each group of interest on that month . 

Limitations of PHC dataset
^^^^^^^^^^^^^^^^^^^^^^^^^^

Currently this dataset has a few relevant limitations, that will probably be solved in the next couple of years.

One limitation is the availability of data. In Brazil 49.2% of the cities report full usage of the standard electronic health record, a scenario that would allow health authorities to monitor the whole city weekly. 

The other 50.8% use either paper based records or non-standard software, implying that information can be entered in local SISAB with up to forty days of delay for routine billing, making it useless to support early warning systems. MoH also limits the availability of data, releasing reports for public access with 3 months of delay and reporting only monthly cases by city. Weekly reports by facility with no delay would be feasible with current MoH infodata structure, and would greatly support local usage of this data for health surveillance.

Finally, it is essential to note that SISAB was designed for governance and accountability purposes. Thus it does not carry the entire patient’s electronic health record. 

Detailed information on symptoms, tests, and treatments is unavailable at this level, leading to imprecision in classifying cases. Disease codes could suffice for an early warning, but more information will be needed for outbreak investigation. 


Variable list for PHC database
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| Original field name     | Field label                               | Type   | Category                              | Description                              | DB Source   |        
+=========================+===========================================+========+=======================================+==========================================+=============+
| uf                      | States and Federal District               | String | Uncategorized                         | States and Federal District              | SISAB       | 
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| ibge                    | City code                                 | Number | Uncategorized                         | City code                                | IBGE        |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| municipio               | City name                                 | String | Uncategorized                         | City name                                | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| atendimentos            | Total PHC Encounters                      | Number | Uncategorized                         | Total PHC Encounters                     | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| populacao_estimada      | Population on that year                   | Number | Uncategorized                         | Population on that year                  | IBGE        | 
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| ano                     | Year                                      | date   | Uncategorized                         | Year                                     | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| mes                     | Month                                     | date   | Uncategorized                         | Month                                    | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| gripal                  | Upper Respiratory Infections              | Number | Uncategorized                         | Upper Respiratory Infections             | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| relacionada             | Other acute symptoms and syndromes        | Number | Uncategorized                         | Other acute symptoms and syndromes       | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| pulmonar                | Lower respiratory infections              | Number | Uncategorized                         | Lower respiratory infections             | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| nao_relacionada         | Other reasons for encounters              | Number | Uncategorized                         | Other reasons for encounters             | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| confundidor             | Seasonal confounding conditions           | Number | Uncategorized                         | Seasonal confounding conditions          | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| pc_cobertura_sf         | Estimated coverage of family health teams | Number | Uncategorized                         | Estimated coverage of family health teams| e-Gestor APS|
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| pc_cobertura_ab         | Estimated coverage of all PHC Teams       | Number | Uncategorized                         | Estimated coverage of all PHC Teams      | e-Gestor APS|
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| porte_municipio         | City Size Category                        | String | >= 0 and <= 25000: pequeno (small)    | City Size Category                       | IBGE        |
+                         +                                           +        +                                       +                                          +             +
|                         |                                           |        | > 25000 and <= 100000: médio (medium) |                                          |             |
+                         +                                           +        +                                       +                                          +             +
|                         |                                           |        | > 100000 and <= 500000: grande (big)  |                                          |             |
+                         +                                           +        +                                       +                                          +             +
|                         |                                           |        | > 500000 : metrópole (metropolis)     |                                          |             |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| ubs_count               | Primary Healthcare Facilities in the city | Number | Uncategorized                         | Primary Healthcare Facilities in the city| SCNES       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
|cod_regiao_de_saude      | Federal Health Region Code                | Number | Uncategorized                         | Federal Health Region Code               | SAGE        |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| nome_da_regiao_de_saude | Federal Health Region Name                | String | Uncategorized                         | Federal Health Region Name               | SAGE        | 
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| long                    | Longitude of city hall                    | Number | Uncategorized                         | Longitude of city hall                   | IBGE        |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| lat                     | Latitude of city hall                     | Number | Uncategorized                         | Latitude of city hall                    | IBGE        |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| area_km2                | Area of the city in square kilometres     | Number | Uncategorized                         | Area of the city in square kilometres    | IBGE        |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| alergias                | Confounding seasonal allergies            | Number | Uncategorized                         | Confounding seasonal allergies           | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+
| dengue                  | Confounding arboviruses                   | Number | Uncategorized                         | Confounding arboviruses                  | SISAB       |
+-------------------------+-------------------------------------------+--------+---------------------------------------+------------------------------------------+-------------+


.. rubric:: References

V.A. Oliveira , A.P. Sironi, I. Marcilio, P.T.V. Florentino, T. C. Silva, R. F. Ortiz, T. M. Machado, G.O. Penna, M.E. Barreto, M. B. Netto,  Syndromic detection of upper respiratory infections in Primary Healthcare as a candidate for Covid-19 early warning in Brazil. A retrospective ecological study. Preprint Available at SSRN: http://dx.doi.org/10.2139/ssrn.4364869, 2023.


**Contributors**

+-------------------+-----------------------------------------------------------------+
| Vinicius Oliveira | Center for Data and Knowledge Integration for Health (CIDACS),  | 
+                   +                                                                 +
|                   | Instituto Gonçalo Moniz, Fundação Oswaldo Cruz, Salvador, Brazil|
+-------------------+-----------------------------------------------------------------+    


