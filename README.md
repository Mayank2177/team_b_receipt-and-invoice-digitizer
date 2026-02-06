# Receipt-and-Invoice-Digitizer

### Description:

**MyDigiBill** is an automated receipt and invoice digitization system that inputs images/document through multiple formats (jpg, png, pdf), preprocesses them for optimal quality, and uses OCR technology (Tesseract) to extract text. An NLP-based extraction + regex engine then intelligently identifies and structures key fields like vendor details, line items, amounts, dates, and taxes into a standardized database format. The system validates extracted data against business rules, stores it in a searchable database with original image references, and provides API integration with popular accounting/ERP systems along with a user-friendly dashboard for review, search, analytics, and export capabilities—ultimately eliminating manual data entry, reducing errors, and enabling real-time financial insights.

### Features:

- **Multi-format Support**: Process JPG, PNG, and PDF documents
- **Advanced Preprocessing**: Automatic image enhancement for optimal OCR accuracy
- **OCR Technology**: Powered by Tesseract for reliable text extraction
- **Intelligent Extraction**: NLP-based field identification with regex validation
- **Structured Data**: Automatically extracts vendor details, line items, amounts, dates, and taxes
- **Data Validation**: Business rule validation for data integrity
- **Database Storage**: Searchable database with original image references
- **API Integration**: Connect with popular accounting/ERP systems
- **User Dashboard**: Intuitive interface for review, search, and analytics
- **Export Capabilities**: Generate reports and export data in multiple formats

### Prerequisites:

Before running the application, ensure you have the following installed:

- **Python**: Version 3.8 or higher
- **pip**: Python package manager
- **Tesseract OCR**: Required for text extraction
  - **Windows**: Download from https://github.com/UB-Mannheim/tesseract/wiki
  - **macOS**: `brew install tesseract`
  - **Linux**: `sudo apt-get install tesseract-ocr`
- **Git**: For cloning the repository

### Steps to Run the App (on your system):

#### 1. Clone the Repository

```bash
git clone https://github.com/Mayank2177/team_b_receipt-and-invoice-digitizer.git
cd team_b_receipt-and-invoice-digitizer
```

#### 2. Create a Virtual Environment

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

#### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

#### 4. Configure Tesseract Path (Windows only)

If you're on Windows, update the Tesseract path in your configuration or code:

```python
import pytesseract
pytesseract.pytesseract.pytesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
```

#### 5. Set Environment Variables

Create a `.env` file in the root directory:

```
DATABASE_URL=sqlite:///mydibill.db
TESSERACT_PATH=/path/to/tesseract
API_KEY=your_api_key_here
```

#### 6. Initialize the Database

```bash
python setup_database.py
```

#### 7. Run the Application

```bash
# For development
python app.py

# For production
gunicorn app:app
```

The application will be available at `http://localhost:5000`

### Usage:

1. **Upload Document**: Use the dashboard to upload receipt or invoice images/PDFs
2. **View Extracted Data**: The system automatically extracts and displays key information
3. **Review & Validate**: Review extracted fields and correct any errors
4. **Export Data**: Export extracted information to CSV, Excel, or integrate with your ERP system

### Project Structure:

```
team_b_receipt-and-invoice-digitizer/
├── app.py                          # Main application entry point
├── requirements.txt                # Python dependencies
├── README.md                       # This file
├── LICENSE                         # Project license
├── config/
│   └── config.py                   # Configuration settings
├── src/
│   ├── preprocessing/              # Image preprocessing modules
│   ├── ocr/                        # OCR extraction logic
│   ├── extraction/                 # NLP and regex-based field extraction
│   ├── validation/                 # Data validation rules
│   └── database/                   # Database models and operations
├── templates/                      # HTML templates for web interface
├── static/                         # CSS, JavaScript, and static assets
├── tests/                          # Unit and integration tests
└── docs/                           # Additional documentation
```

### API Endpoints:

- `POST /api/upload` - Upload a document
- `GET /api/documents/<id>` - Retrieve extracted data
- `PUT /api/documents/<id>` - Update extracted data
- `DELETE /api/documents/<id>` - Delete a document
- `GET /api/documents` - List all documents with pagination
- `POST /api/export` - Export data

### Testing:

```bash
# Run unit tests
pytest tests/

# Run with coverage
pytest --cov=src tests/
```

### Troubleshooting:

| Issue | Solution |
|-------|----------|
| Tesseract not found | Ensure Tesseract is installed and path is correctly configured |
| OCR accuracy issues | Use high-quality images (300+ DPI) and ensure good lighting |
| Database errors | Check database connection string in .env file |
| Module not found | Run `pip install -r requirements.txt` again |

### Contributing:

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

### License:

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### Contact & Support:

For questions, issues, or suggestions, please:
- Open an issue on GitHub
- Contact the development team via the repository

### Roadmap:

- [ ] Multi-language OCR support
- [ ] Machine learning-based field extraction
- [ ] Real-time batch processing
- [ ] Mobile application
- [ ] Integration with additional ERP systems
- [ ] Advanced analytics dashboard

---

**Last Updated**: 2026-02-06 17:17:26  
**Version**: 1.0.0