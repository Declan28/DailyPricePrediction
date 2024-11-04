import { Component } from '@angular/core';

@Component({
  selector: 'app-file-comparison',
  template: `
    <div class="container">
      <div class="header">
        <h1>Morgan Stanley | AI@MS+</h1>
      </div>

      <div class="file-comparison">
        <h2>File Comparison</h2>
        <p>07:48 AM</p>
        
        <form>
          <div class="step">
            <label>Step 1: Upload content</label>
            <div class="upload-box">
              <input type="file" (change)="onFileSelected($event)" />
              <p>Drag and drop file here, or <a href="#">Browse</a></p>
              <small>PDF, PPT, or Word doc (25MB Max)</small>
            </div>
            <div class="upload-box">
              <input type="file" (change)="onFileSelected($event)" />
              <p>Drag and drop file here, or <a href="#">Browse</a></p>
              <small>PDF, PPT, or Word doc (25MB Max)</small>
            </div>
          </div>
          
          <div class="step">
            <label>Step 2: Select action</label>
            <select [(ngModel)]="selectedAction">
              <option value="identify">Identify differences</option>
              <option value="merge">Merge documents</option>
            </select>
          </div>

          <button type="button" (click)="onContinue()">Continue</button>
        </form>
      </div>

      <div class="footer">
        <textarea placeholder="Type a message"></textarea>
      </div>
    </div>
  `,
  styles: [`
    .container {
      max-width: 600px;
      margin: auto;
      font-family: Arial, sans-serif;
      background-color: #f9f9f9;
      padding: 20px;
      border: 1px solid #ddd;
      border-radius: 8px;
    }

    .header {
      text-align: center;
      background-color: #002855;
      color: white;
      padding: 15px;
      border-radius: 8px 8px 0 0;

      h1 {
        font-size: 24px;
        margin: 0;
      }
    }

    .file-comparison {
      padding: 15px;
      h2 {
        font-size: 20px;
      }

      .step {
        margin: 20px 0;

        label {
          font-weight: bold;
          display: block;
          margin-bottom: 10px;
        }

        .upload-box {
          border: 2px dashed #aaa;
          padding: 20px;
          text-align: center;
          cursor: pointer;

          input[type="file"] {
            display: none;
          }

          a {
            color: #0066cc;
            text-decoration: underline;
          }

          small {
            display: block;
            margin-top: 10px;
            color: #666;
          }
        }

        select {
          width: 100%;
          padding: 10px;
          border: 1px solid #ddd;
          border-radius: 5px;
          margin-top: 10px;
        }
      }

      button {
        background-color: #0056b3;
        color: white;
        padding: 10px 15px;
        border: none;
        border-radius: 5px;
        cursor: pointer;

        &:hover {
          background-color: #003d80;
        }
      }
    }

    .footer {
      margin-top: 20px;

      textarea {
        width: 100%;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 5px;
        height: 50px;
      }
    }
  `]
})
export class FileComparisonComponent {
  selectedAction: string = 'identify';

  onFileSelected(event: any) {
    const file = event.target.files[0];
    if (file) {
      console.log('File selected:', file.name);
    }
  }

  onContinue() {
    console.log('Selected action:', this.selectedAction);
  }
}
