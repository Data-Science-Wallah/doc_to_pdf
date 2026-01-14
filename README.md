# 📄 DOCX to PDF Converter

A professional Streamlit web application that allows users to upload DOCX files and convert them to PDF format using LibreOffice. This tool provides a simple, fast, and reliable way to perform document conversions directly in the browser.

**Created by Data Science Wallah** - Follow us for more amazing projects!

## 🚀 Features

- **Easy Upload**: Drag and drop or select DOCX files for conversion
- **Instant Conversion**: Powered by LibreOffice for high-quality PDF output
- **Download Ready**: Get your PDF with one click
- **Conversion Time Tracking**: See how long the conversion takes
- **File Information**: View original file name and PDF size
- **Professional UI**: Clean, modern interface with responsive design
- **Error Handling**: Validates DOCX files and provides clear error messages

## 📋 Requirements

- Python 3.7+
- LibreOffice (must be installed on the system)
- macOS/Linux/Windows

## 🛠️ Installation

1. **Clone the repository:**
   ```bash
   [git clone https://github.com/your-username/docx-to-pdf-converter.git](https://github.com/Data-Science-Wallah/doc_to_pdf.git)
   cd docx-to-pdf-converter
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Install LibreOffice:**
   - **macOS:** `brew install --cask libreoffice`
   - **Ubuntu/Debian:** `sudo apt-get install libreoffice`
   - **Windows:** Download from [libreoffice.org](https://www.libreoffice.org/)

## 🚀 Usage

1. **Run the application:**
   ```bash
   streamlit run doc_to_pdf.py
   ```

2. **Open your browser:**
   Navigate to `http://localhost:8501`

3. **Convert documents:**
   - Click "Choose a DOCX file" to upload
   - Wait for conversion to complete
   - Download the PDF using the download button

## 📁 Project Structure

```
├── doc_to_pdf_converter.py# Main Streamlit application
├── requirements.txt       # Python dependencies
├── README.md             # This file
└── temp/                 # Temporary files (auto-created)
```

## 🔧 Configuration

The application uses system temporary directories for processing files. No additional configuration is required.

## 🐛 Troubleshooting

### Common Issues:

1. **"Conversion failed: Error: Message not understood."**
   - Ensure LibreOffice is properly installed
   - Check that the DOCX file is not corrupted
   - Try with a different DOCX file

2. **Application won't start**
   - Verify all dependencies are installed
   - Check Python version (3.7+ required)

3. **Large files not converting**
   - The app handles files up to typical document sizes
   - For very large files, ensure sufficient system memory

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Streamlit](https://streamlit.io/) for the web framework
- [LibreOffice](https://www.libreoffice.org/) for PDF conversion
- [python-docx](https://python-docx.readthedocs.io/) for DOCX handling

## 📞 Support

If you encounter any issues or have questions, please open an issue on GitHub.

## 📞 Contact

For any queries, collaborations, or feedback, reach out to us:

- **Follow us on social media:** Follow us [@datasciencewallah](https://instagram.com/datasciencewallah) |  Subscribe for more projects | [@datasciencewallah](https://youtube.com/@datasciencewallah) |Reach out for collaborations!
- **Subscribe to our channel** for more tutorials and projects
- **Collaborate with us** on exciting data science and AI projects

---

**Built with ❤️ by Data Science Wallah using Streamlit and LibreOffice**
