---
layout: page
title:  Biomarker Analyzer 
description: Transforming Medical Lab Reports into Actionable Insights
img: assets/img/12.jpg
importance: 1
category: work
related_publications: #true
---
In the realm of healthcare, tracking and analyzing biomarker trends over time is crucial for both healthcare providers and patients. Today, I'm excited to introduce the Biomarker Analyzer, a sophisticated yet user-friendly Streamlit application that transforms static PDF lab reports into dynamic, visual insights.

## The Challenge

Healthcare professionals and patients often face several challenges when dealing with medical lab reports:

- Multiple PDF reports scattered across different dates
- Manual data entry for trend analysis
- Difficulty in visualizing changes over time
- Handling different date formats (BS/AD)
- Extracting consistent data from varying report formats

The Biomarker Analyzer addresses these challenges by providing an automated solution that makes biomarker analysis accessible and intuitive.

## Key Features

### 1. Intelligent PDF Processing
The application leverages `pdfplumber` to extract text from PDF lab reports with remarkable accuracy. It uses sophisticated regular expressions to identify and extract:
- Patient demographics (name, number, age, and gender)
- Report dates
- Biomarker measurements and their units

### 2. Smart Date Handling
One unique feature is the application's ability to handle both AD (Gregorian) and BS (Bikram Sambat) date formats:
- Automatically detects BS dates based on year thresholds
- Converts BS dates to AD format using the `nepali_datetime` library
- Ensures consistent date formatting across all reports

### 3. Interactive Data Visualization
The visualization system is built with a focus on clarity and usability:
- Multiple biomarkers can be plotted on the same graph for comparison
- Interactive plots with zoom and hover capabilities
- Clear legends and labels for easy interpretation
- Grid lines for better readability
- Customizable plot selections

### 4. User-Friendly Interface
The Streamlit-based interface offers:
- Clear instructions for users
- Multiple file upload capability
- Organized display of patient information
- Expandable/collapsible plot sections
- Interactive biomarker selection
- Tabular view of extracted data

## Technical Implementation

### Data Extraction
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

### Data Processing
The application processes the extracted data through several steps:
1. Creation of structured DataFrames
2. Date normalization and sorting
3. Numerical value validation
4. Unit standardization

### Visualization Engine
The plotting system uses Matplotlib with customized styling:
- Enhanced readability with the 'ggplot' style
- Consistent marker and line styles
- Optimized figure sizes
- Responsive layout adjustments

## Use Cases

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

## Future Enhancements

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

## Conclusion

The Biomarker Analyzer represents a significant step forward in making medical lab data more accessible and actionable. By automating the extraction and visualization of biomarker data, it enables healthcare providers and patients to focus on what matters most: understanding and acting on health trends.

Whether you're a healthcare provider looking to streamline your workflow or a patient wanting to take control of your health data, the Biomarker Analyzer offers a powerful, user-friendly solution for transforming static lab reports into dynamic, actionable insights.

The open-source nature of this project means it can continue to evolve and improve with community input, making it an increasingly valuable tool in the healthcare technology ecosystem.
