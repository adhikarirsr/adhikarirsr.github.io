---
layout: page
title:  Biomarker Analyzer 
description: Transforming Medical Lab Reports into Actionable Insights
img: assets/img/biomarker.png
importance: 1
category: work
related_publications: #true
---
## The Story Behind the Biomarker Analyzer

### A Personal Journey

The catalyst for this project arose from a devastating family emergency. My aunt was found unconscious in her bedroom and was rushed to the Tribhuvan University Teaching Hospital (TUTH). She was immediately transferred to the ICU, where she would spend the next 39 days. During that time, I was unable to speak with her, as she remained unconscious. I don’t even know if she fought for her life. To be honest, I’m uncertain whether she had the will to fight or if she understood that she needed to. Tragically, she passed away.

### The Challenge

During the anxiety-filled days in the ICU, our family faced two significant challenges: the emotional burden of watching a loved one in critical care and the frustrating struggle to understand her medical condition. Eventually, we discovered that her medical records could be accessed through [merodoctor.com](https://labreport.merodoctor.com/). However, the data was only available in PDF format—static, difficult to analyze, and challenging to track over time.

This experience highlighted a critical gap in our healthcare system: despite having access to advanced medical tests and monitoring, the ability to meaningfully track and understand these results over time remains a significant challenge for both families and healthcare providers.

Our situation underscored the need for better tools to interpret and analyze medical data. By leveraging the power of Large Language Models (LLMs), I was able to develop a tool that aimed to address this issue.

### The Solution

The Biomarker Analyzer emerged with a clear mission: to transform the way we visualize the medical data, making it more accessible, understandable, and actionable. This Streamlit application converts static PDF lab reports into dynamic, visual insights, enabling both healthcare providers and families to better track and understand biomarker trends over time.

### Looking Forward

While the current version of the Biomarker Analyzer represents a step forward, I acknowledge that this is just the beginning. There's still much work to be done and numerous possibilities for enhancement. I hope this project can serve as a foundation for others to build upon, potentially creating even more comprehensive solutions for healthcare data interpretation and analysis.

Through this journey, one thing has become clear: there has a lot that has to be done and if we want to have an impact in Nepal, we don't need a quantum leap. 

### The Challenge

Healthcare professionals and patients often face several challenges when dealing with medical lab reports:

- Multiple PDF reports scattered across different dates
- Manual data entry for trend analysis
- Difficulty in visualizing changes over time
- Handling different date formats (BS/AD)
- Extracting consistent data from varying report formats

The Biomarker Analyzer addresses these challenges by providing an automated solution that makes biomarker analysis accessible and intuitive.

### Key Features

#### 1. PDF Processing
The application leverages `pdfplumber` to extract text from PDF lab reports with remarkable accuracy. It uses sophisticated regular expressions to identify and extract:
- Patient demographics (name, number, age, and gender)
- Report dates
- Biomarker measurements and their units

#### 2. Date Handling
One unique feature is the application's ability to handle both AD (Gregorian) and BS (Bikram Sambat) date formats:
- Automatically detects BS dates based on year thresholds
- Converts BS dates to AD format using the `nepali_datetime` library
- Ensures consistent date formatting across all reports

#### 3. Interactive Data Visualization
The visualization system is built with a focus on clarity and usability:
- Multiple biomarkers can be plotted on the same graph for comparison
- Interactive plots with zoom and hover capabilities
- Clear legends and labels for easy interpretation
- Grid lines for better readability
- Customizable plot selections

#### 4. User-Friendly Interface
The Streamlit-based interface offers:
- Clear instructions for users
- Multiple file upload capability
- Organized display of patient information
- Expandable/collapsible plot sections
- Interactive biomarker selection
- Tabular view of extracted data

### Technical Implementation

#### Data Extraction
The core of the application is the `extract_data_from_pdf` function, which:
1. Extracts text from each page of the PDF
2. Uses regular expressions to identify key information
3. Normalizes biomarker names and units
4. Converts numerical values to appropriate formats

```python
def extract_data_from_pdf(pdf_file):
    # Extract text from PDF
    with pdfplumber.open(pdf_file) as pdf:
        text = ""
        for page in pdf.pages:
            text += page.extract_text() + "\n"
```

#### Data Processing
The application processes the extracted data through several steps:
1. Creation of structured DataFrames
2. Date normalization and sorting
3. Numerical value validation
4. Unit standardization

#### Visualization Engine
The plotting system uses Matplotlib with customized styling:
- Enhanced readability with the 'ggplot' style
- Consistent marker and line styles
- Optimized figure sizes
- Responsive layout adjustments

### Use Cases

The Biomarker Analyzer is particularly useful for:

1. **Healthcare Providers**
   - Track patient progress over time
   - Identify trends and patterns
   - Generate visual reports for patient consultations

2. **Patients**
   - Monitor their health markers
   - Better understand their test results
   - Keep organized records of their lab reports

3. **Research**
   - Aggregate and analyze biomarker data
   - Generate visualizations for studies
   - Export processed data for further analysis

### Future Enhancements

While the current version of the Biomarker Analyzer is already powerful, several enhancements could make it even more valuable:

1. **Advanced Analytics**
   - Statistical analysis of trends
   - Anomaly detection
   - Reference range visualization

2. **Export Capabilities**
   - PDF report generation
   - Data export in various formats
   - Shareable links for healthcare providers

3. **Integration Features**
   - Electronic Health Record (EHR) system integration
   - Mobile app compatibility
   - Cloud storage support

### A Call to Action
If you're a healthcare provider, researcher, or someone who has faced similar challenges in understanding medical data, I invite you to contribute to this project. Whether through feedback, code contributions, or simply sharing your story, every input helps us make this tool more effective for those who need it most.
Together, we can work towards a future where medical data is not just accessible, but truly meaningful for both healthcare providers and families during their most challenging moments.

The open-source nature of this project means it can continue to evolve and improve with community input, making it an increasingly valuable tool in the healthcare technology ecosystem.
