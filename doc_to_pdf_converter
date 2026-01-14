"""Streamlit DOCX → PDF converter.
What this app does
- Upload a DOCX.
- Convert it to PDF.
- Show a quick text preview extracted from the DOCX.
- Provide a download button for the PDF.
Implementation notes
- DOCX to PDF conversion: `docx2pdf` (requires LibreOffice)
- Preview: text extracted from the uploaded DOCX
"""
from __future__ import annotations
import os
import tempfile
from io import BytesIO
import streamlit as st
from docx import Document
import base64
import subprocess
import streamlit.components.v1 as components
import time

def convert_docx_bytes_to_pdf(docx_bytes: bytes) -> tuple[bytes, str]:
    """Convert DOCX bytes to PDF bytes.
    Returns:
        (pdf_bytes, debug_message)
    """
    import uuid
    try:
        Document(BytesIO(docx_bytes))
    except Exception as e:
        raise ValueError(f"Invalid DOCX file: {e}")
    temp_dir = os.path.join(tempfile.gettempdir(), "doc_to_pdf_temp")
    os.makedirs(temp_dir, exist_ok=True)
    docx_path = os.path.join(temp_dir, f"temp_docx_{uuid.uuid4()}.docx")
    pdf_path = os.path.join(temp_dir, f"temp_pdf_{uuid.uuid4()}.pdf")
    try:
        with open(docx_path, "wb") as f:
            f.write(docx_bytes)
        cmd = ['soffice', '--headless', '--convert-to', 'pdf:writer_pdf_Export', docx_path, '--outdir', temp_dir]
        result = subprocess.run(cmd, capture_output=True, text=True)
        if result.returncode != 0:
            raise ValueError(f"Conversion failed: {result.stderr}")
        pdf_path = os.path.join(temp_dir, os.path.splitext(os.path.basename(docx_path))[0] + '.pdf')
        with open(pdf_path, "rb") as f:
            return f.read(), "Converted with soffice"
    finally:
        for p in (docx_path, pdf_path):
            try:
                if os.path.exists(p):
                    os.unlink(p)
            except OSError:
                pass

def docx_text_preview(docx_bytes: bytes, max_paragraphs: int = 20) -> str:
    """Extract a plain-text preview from DOCX bytes."""
    doc = Document(BytesIO(docx_bytes))
    out = []
    for p in doc.paragraphs:
        t = (p.text or "").strip()
        if t:
            out.append(t)
        if len(out) >= max_paragraphs:
            break
    return "\n".join(out)

def main() -> None:
    st.set_page_config(page_title="Data Science Wallah DOCX → PDF Converter", page_icon="📄", layout="wide")
    st.markdown("""
    <style>
    .main { background-color: #f0f2f6; }
    .stButton>button { background-color: #4CAF50; color: white; border-radius: 5px; }
    .stSuccess { background-color: #d4edda; color: #155724; }
    .stCaption { font-size: 14px; }
    </style>
    """, unsafe_allow_html=True)
    st.markdown("# Built with ❤️ by Data Science Wallah 📄 DOCX to PDF Converter")
    st.markdown("---")
    st.markdown("Upload your DOCX file and convert it to PDF instantly. This app uses LibreOffice for high-quality conversion.")
    uploaded = st.file_uploader("Choose a DOCX file", type=["docx"])
    if not uploaded:
        st.info("Please upload a DOCX file to start the conversion.")
        return
    docx_bytes = uploaded.getvalue()
    with st.spinner("Converting DOCX to PDF..."):
        start_time = time.time()
        pdf_bytes, debug = convert_docx_bytes_to_pdf(docx_bytes)
        end_time = time.time()
        conversion_time = end_time - start_time
    st.success("✅ Conversion completed successfully!")
    st.caption(f"{debug} | ⏱️ Conversion time: {conversion_time:.2f} seconds")
    col1, col2 = st.columns([1, 1])
    with col1:
        st.subheader("📥 Download PDF")
        out_name = os.path.splitext(uploaded.name)[0] + ".pdf"
        st.download_button(
            label="Download PDF",
            data=pdf_bytes,
            file_name=out_name,
            mime="application/pdf",
            use_container_width=True,
        )
    with col2:
        st.subheader("📊 File Info")
        st.write(f"**Original File:** {uploaded.name}")
        st.write(f"**PDF Size:** {len(pdf_bytes)} bytes")
    st.markdown("---")
    st.markdown("Built with ❤️ by **Data Science Wallah** using Streamlit and LibreOffice.")
    st.markdown("Follow us [@datasciencewallah](https://instagram.com/datasciencewallah) |  Subscribe for more projects | [@datasciencewallah](https://youtube.com/@datasciencewallah) |Reach out for collaborations!")

if __name__ == "__main__":
    main()
