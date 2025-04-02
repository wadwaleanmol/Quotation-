<!DOCTYPE html>
<html>
<head>
    <title>Quotation System</title>
    <style>
        /* ... (Your existing styles) ... */

        .green-button {
            background-color: green;
            color: white;
            padding: 10px 20px;
            border: none;
            cursor: pointer;
        }

        .header {
            display: flex;
            justify-content: center;
            padding: 10px;
            background-color: #f0f0f0;
        }

        .header-title {
            font-size: 24px;
            font-weight: bold;
            text-align: center;
        }

        .header-title span:nth-child(1) { color: cyan; }
        .header-title span:nth-child(2) { color: magenta; }
        .header-title span:nth-child(3) { color: yellow; }
        .header-title span:nth-child(4) { color: black; }

        .main-content {
            display: flex;
        }

        .left-menu {
            width: 200px;
            padding: 10px;
            background-color: #e0e0e0;
        }

        .center-content {
            flex-grow: 1;
            padding: 20px;
            background-color: #f9f9f9;
        }

        .right-content {
            width: 300px;
            padding: 10px;
            background-color: #f8f8f8;
        }

        .quotation-list {
            list-style: none;
            padding: 0;
        }

        .quotation-list li {
            padding: 5px;
            border-bottom: 1px solid #ccc;
            cursor: pointer;
        }

        .quotation-list li:last-child {
            border-bottom: none;
        }

        #quotationFormContainer {
          background-color: #e8f5e9;
          padding: 15px;
          border-radius: 5px;
        }

        #quotationHistory li:nth-child(even) {
            background-color: #e0f7fa;
        }
    </style>
</head>
<body>

    <div class="header">
        <div class="header-title">
            <span>A</span><span>R</span><span>T</span><span>Y</span> OFFSET
        </div>
        <div></div>
    </div>

    <div class="main-content">
        <div class="left-menu">
            <ul>
                <li><a href="#" onclick="showQuotationForm()">Create Quotation</a></li>
                <li><a href="#" onclick="loadQuotationHistory()">Quotation History</a></li>
                <li>My Account</li>
                <li><a href="#" onclick="showBookQuotationForm()">Quotation for Book</a></li>
            </ul>
        </div>

        <div class="center-content">
            <button onclick="showQuotationForm()">Create New Quotation</button>

            <div id="quotationFormContainer" style="display: none;">
                <form id="quotationForm">
                    <label for="customerName">Customer Name:</label>
                    <input type="text" id="customerName" name="customerName" required><br><br>

                    <label for="customerNumber">Customer Number:</label>
                    <input type="text" id="customerNumber" name="customerNumber" required><br><br>

                    <label for="jobType">Job Type:</label>
                    <input type="text" id="jobType" name="jobType" value="Pamphlet" readonly><br><br>

                    <label for="jobSize">Job Size:</label>
                    <select id="jobSize" name="jobSize">
                        <option value="A4">A4</option>
                        <option value="A4(letter size)">A4 (Letter Size)</option>
                        <option value="A/4">A/4</option>
                        <option value="A/8">A/8</option>
                        <option value="A/5">A/5</option>
                        <option value="A/2">A/2</option>
                    </select><br><br>

                    <label for="jobQuantity">Job Quantity:</label>
                    <input type="number" id="jobQuantity" name="jobQuantity" required><br><br>

                    <label for="ups">Ups:</label>
                    <select id="ups" name="ups">
                        <option value="2">2</option>
                        <option value="3">3</option>
                        <option value="4">4</option>
                        <option value="5">5</option>
                        <option value="6">6</option>
                        <option value="7">7</option>
                        <option value="8">8</option>
                        <option value="9">9</option>
                        <option value="10">10</option>
                    </select><br><br>

                    <label for="paperType">Paper Type:</label>
                    <select id="paperType" name="paperType">
                        <option value="90 Art">90 Art</option>
                        <option value="70 Map">70 Map</option>
                        <option value="130 Art">130 Art</option>
                    </select><br><br>

                    <label for="printingSize">Printing Size:</label>
                    <select id="printingSize" name="printingSize">
                        <option value="18*23">18*23</option>
                        <option value="18*25">18*25</option>
                        <option value="15*20">15*20</option>
                        <option value="20*30">20*30</option>
                        <option value="12*25">12*25</option>
                    </select><br><br>

                    <label for="paperSize">Paper Size:</label>
                    <select id="paperSize" name="paperSize">
                        <option value="18*23">18*23</option>
                        <option value="18*25">18*25</option>
                        <option value="23*36">23*36</option>
                        <option value="25*36">25*36</option>
                        <option value="20*30">20*30</option>
                    </select><br><br>

                    <label for="printingSheetQuantity">Printing Sheet Quantity:</label>
                    <input type="number" id="printingSheetQuantity" name="printingSheetQuantity" readonly><br><br>

                    <label for="paperRate">Paper Rate:</label>
                    <input type="number" id="paperRate" name="paperRate" required><br><br>

                    <label for="paperAmount">Paper Amount:</label>
                    <input type="number" id="paperAmount" name="paperAmount" readonly><br><br>

                    <label for="printingCost">Printing Cost:</label>
                    <input type="number" id="printingCost" name="printingCost" required><br><br>

                    <label for="thousandCost">Next Thousand Cost:</label>
                    <input type="number" id="thousandCost" name="thousandCost" required><br><br>

                    <label for="cuttingCost">Cutting Cost:</label>
                    <input type="number" id="cuttingCost" name="cuttingCost" required><br><br>

                    <label for="transportationCost">Transportation Cost:</label>
                    <input type="number" id="transportationCost" name="transportationCost" required><br><br>

                    <label for="laminationCost">Lamination Cost:</label>
                    <input type="number" id="laminationCost" name="laminationCost" required><br><br>

                    <label for="totalCost">Total Cost:</label>
                    <input type="number" id="totalCost" name="totalCost" readonly><br><br>

                    <button type="button" onclick="processQuotation()" class="green-button">Create Quotation</button>
                </form>

            </div>

            <div id="bookQuotationFormContainer" style="display: none;">
                <h2>Book Quotation Form</h2>
                <form id="bookQuotationForm">
                    <label for="bookCustomerName">Customer Name:</label>
                    <input type="text" id="bookCustomerName" name="bookCustomerName" required><br><br>
                    <label for="bookCustomerNumber">Customer Number:</label>
                    <input type="text" id="bookCustomerNumber" name="bookCustomerNumber" required><br><br>
                    <label for="bookTitle">Book Title :</label>
                    <input type="text" id="bookTitle" name="bookTitle" required><br><br>
                    <label for="bookPages">Number of Pages :</label>
                    <input type="number" id="bookPages" name="bookPages" required><br><br>
                    <label for="bookPagesInSheet">No. of Pages in Sheet:</label>
                    <input type="number" id="bookPagesInSheet" name="bookPagesInSheet" required onchange="calculateForms()"><br><br>
                    <label for="bookForms">No. of Forms:</label>
                    <input type="number" id="bookForms" name="bookForms" readonly><br><br>
                    <label for="bookQuantity">Book Quantity :</label>
                    <input type="number" id="bookQuantity" name="bookQuantity" required onchange="calculateBindingCost(); calculateSheetsRequired(); calculatePaperCost()"><br><br>
                    <label for="bookSheetsRequired">No. of Sheets Required :</label>
                    <input type="number" id="bookSheetsRequired" name="bookSheetsRequired" readonly><br><br>
                    <label for="bookPaperType">Paper Type:</label>
                    <select id="bookPaperType" name="bookPaperType">
                        <option value="90 Art">90 Art</option>
                        <option value="70 Map">70 Map</option>
                        <option value="130 Art">130 Art</option>
                    </select><br><br>
                    <label for="bookPaperSize">Paper Size:</label>
                    <select id="bookPaperSize" name="bookPaperSize">
                        <option value="18*23">18*23</option>
                        <option value="18*25">18*25</option>
                        <option value="23*36">23*36</option>
                        <option value="25*36">25*36</option>
                        <option value="20*30">20*30</option>
                    </select><br><br>
                    <label for="bookCoverType">Cover Type:</label>
                    <select id="bookCoverType" name="bookCoverType">
                        <option value="NA">NA</option>
                        <option value="300 Art">300 Art</option>
                        <option value="350 Art">350 Art</option>
                        <option value="170 Art">170 Art</option>
                        <option value="250 Art">250 Art</option>
                    </select><br><br>
                    <label for="bookPaperRate">Paper Rate:</label>
                    <input type="number" id="bookPaperRate" name="bookPaperRate" required onchange="calculatePaperCost()"><br><br>
                    <label for="bookPaperCost">Paper Cost:</label>
                    <input type="number" id="bookPaperCost" name="bookPaperCost" readonly><br><br>
                    <label for="bookBindingType">Binding Type:</label>
                    <select id="bookBindingType" name="bookBindingType">
                        <option value="Centre pin">Centre pin</option>
                        <option value="Side pin">Side pin</option>
                        <option value="Prefect binding">Prefect binding</option>
                        <option value="Rimming">Rimming</option>
                        <option value="Section">Section</option>
                    </select><br><br>
                    <label for="bookBindingRate">Binding Rate:</label>
                    <input type="number" id="bookBindingRate" name="bookBindingRate" required onchange="calculateBindingCost()"><br><br>
                    <label for="bookPrintingCost">Printing Cost:</label>
                    <input type="number" id="bookPrintingCost" name="bookPrintingCost" required><br><br>
                    <label for="bookNextThousand">Next Thousand Cost:</label>
                    <input type="number" id="bookNextThousand" name="bookNextThousand"><br><br>
                    <label for="bookLamination">Lamination:</label>
                    <select id="bookLamination" name="bookLamination">
                        <option value="NA">NA</option>
                        <option value="Gloss">Gloss</option>
                        <option value="Matt">Matt</option>
                        <option value="Spot">Spot</option>
                        <option value="Texture">Texture</option>
                        <option value="Pawan">Pawan</option>
                    </select><br><br>
                    <label for="bookLaminationCost">Lamination Cost:</label>
                    <input type="number" id="bookLaminationCost" name="bookLaminationCost"><br><br>
                    <label for="bookBindingCost">Binding Cost:</label>
                    <input type="number" id="bookBindingCost" name="bookBindingCost" readonly><br><br>
                    <label for="bookTotalCost">Total Cost:</label>
                    <input type="number" id="bookTotalCost" name="bookTotalCost" readonly><br><br>
                    <button type="button" onclick="processBookQuotation()" class="green-button">Create Book Quotation</button>
                </form>
            </div>
        </div>

        <div class="right-content">
            <h2>Quotation History</h2>
            <ul id="quotationHistory" class="quotation-list">
            </ul>
        </div>
    </div>

    <script>
        // ... (Your existing JavaScript functions) ...
        function calculateForms() {
            const pages = parseInt(document.getElementById("bookPages").value);
            const pagesInSheet = parseInt(document.getElementById("bookPagesInSheet").value);
            if (!isNaN(pages) && !isNaN(pagesInSheet) && pagesInSheet > 0) {
                document.getElementById("bookForms").value = pages / pagesInSheet;
            } else {
                document.getElementById("bookForms").value = '';
            }
        }

        function calculateBindingCost() {
            const quantity = parseInt(document.getElementById("bookQuantity").value);
            const rate = parseFloat(document.getElementById("bookBindingRate").value);
            if (!isNaN(quantity) && !isNaN(rate)) {
                document.getElementById("bookBindingCost").value = quantity * rate;
            } else {
                document.getElementById("bookBindingCost").value = '';
            }
        }

        function calculateSheetsRequired() {
            const forms = parseFloat(document.getElementById("bookForms").value);
            const quantity = parseInt(document.getElementById("bookQuantity").value);

            if (!isNaN(forms) && !isNaN(quantity)) {
                document.getElementById("bookSheetsRequired").value = forms * quantity;
            } else {
                document.getElementById("bookSheetsRequired").value = '';
            }
        }

        function calculatePaperCost() {
            const sheets = parseFloat(document.getElementById("bookSheetsRequired").value);
            const rate = parseFloat(document.getElementById("bookPaperRate").value);

            if (!isNaN(sheets) && !isNaN(rate)) {
                document.getElementById("bookPaperCost").value = sheets * rate;
            } else {
                document.getElementById("bookPaperCost").value = '';
            }
        }

        function showBookQuotationForm() {
            const form = document.getElementById("bookQuotationFormContainer");
            form.style.display = form.style.display === "none" ? "block" : "none";
            document.getElementById("quotationFormContainer").style.display = "none";
        }

        function processBookQuotation() {
            // Implement the logic to handle the book quotation form data here
            const bookCustomerName = document.getElementById("bookCustomerName").value;
            const bookCustomerNumber = document.getElementById("bookCustomerNumber").value;
            const bookTitle = document.getElementById("bookTitle").value;
            const bookPages = parseInt(document.getElementById("bookPages").value);
            const bookPagesInSheet = parseInt(document.getElementById("bookPagesInSheet").value);
            const bookQuantity = parseInt(document.getElementById("bookQuantity").value);
            const bookPaperType = document.getElementById("bookPaperType").value;
            const bookPaperSize = document.getElementById("bookPaperSize").value;
            const bookCoverType = document.getElementById("bookCoverType").value;
            const bookBindingType = document.getElementById("bookBindingType").value;
            const bookBindingRate = parseFloat(document.getElementById("bookBindingRate").value);
            const bookPrintingCost = parseFloat(document.getElementById("bookPrintingCost").value);
            const bookForms = parseInt(document.getElementById("bookForms").value);
            const bookBindingCost = parseFloat(document.getElementById("bookBindingCost").value);
            const bookLamination = document.getElementById("bookLamination").value;
            const bookLaminationCost = parseFloat(document.getElementById("bookLaminationCost").value);
            const bookSheetsRequired = parseFloat(document.getElementById("bookSheetsRequired").value);
            const bookPaperRate = parseFloat(document.getElementById("bookPaperRate").value);
            const bookPaperCost = parseFloat(document.getElementById("bookPaperCost").value);
            const bookNextThousand = parseFloat(document.getElementById("bookNextThousand").value);

            const bookTotalCost = bookPrintingCost + bookBindingCost + bookLaminationCost + bookPaperCost + bookNextThousand;
            document.getElementById("bookTotalCost").value = bookTotalCost;

            const data = {
                bookCustomerName: bookCustomerName,
                bookCustomerNumber: bookCustomerNumber,
                bookTitle: bookTitle,
                bookPages: bookPages,
                bookPagesInSheet: bookPagesInSheet,
                bookQuantity: bookQuantity,
                bookPaperType: bookPaperType,
                bookPaperSize: bookPaperSize,
                bookCoverType: bookCoverType,
                bookBindingType: bookBindingType,
                bookBindingRate: bookBindingRate,
                bookPrintingCost: bookPrintingCost,
                bookBindingCost: bookBindingCost,
                bookForms: bookForms,
                bookTotalCost: bookTotalCost,
                bookLamination: bookLamination,
                bookLaminationCost: bookLaminationCost,
                bookSheetsRequired: bookSheetsRequired,
                bookPaperRate: bookPaperRate,
                bookPaperCost: bookPaperCost,
                bookNextThousand:bookNextThousand
            };

            fetch("/api/bookQuotation", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                },
                body: JSON.stringify(data),
            })
            .then(response => response.json())
            .then(responseData => {
                console.log("Success:", responseData);
                alert("Book Quotation saved successfully!");
                loadQuotationHistory();
                showBookQuotationForm();
            })
            .catch(error => {
                console.error("Error:", error);
                alert("An error occurred. Please try again.");
            });
        }
        // ... (Your existing JavaScript functions) ...
        function showQuotationForm() {
            const form = document.getElementById("quotationFormContainer");
            form.style.display = form.style.display === "none" ? "block" : "none";
            document.getElementById("bookQuotationFormContainer").style.display = "none";
        }

        // ... (Your existing JavaScript functions) ...
    </script>

</body>
</html>
