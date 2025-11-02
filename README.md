# FUTURE_CS_03
SECURE FILE SHARING SYSTEM

Soruce code


import sys
import PyPDF2 # Import PyPDF2 outside the function


def create_password_protected_pdf(input_pdf, output_pdf, password):
    try:
        with open(input_pdf, 'rb') as pdf_file:
            pdf_reader = PyPDF2.PdfReader(pdf_file)
            pdf_writer = PyPDF2.PdfWriter()

            for page_num in range(len(pdf_reader.pages)):
                pdf_writer.add_page(pdf_reader.pages[page_num])

            pdf_writer.encrypt(password)

            with open(output_pdf, 'wb') as output_file:
                pdf_writer.write(output_file)

            print(f"Password-protected PDF saved as {output_pdf}")

    except FileNotFoundError:
        print(f"The file {input_pdf} was not found.")
    except PyPDF2.utils.PdfReadError:
        print(f"The file {input_pdf} is not a valid PDF.")
    except Exception as e:
        print(f"Error: {e}")

input_pdf = "input.pdf"
output_pdf = "output_protected.pdf"
password = "@hHari87"

create_password_protected_pdf(input_pdf, output_pdf, password)
