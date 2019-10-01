# angularCssDialogModal

# global style.scss


/**
My Dialog Model 
*/
.modal-title {
  display: flex;
  justify-content: flex-start;
}

.modal-title h1 {
  font-family: $my-font-family-roboto-slab-serif;
  font-size: 30px;
  font-weight: bold;
  font-style: normal;
  font-stretch: normal;
  letter-spacing: normal;
  text-align: left;
  color: #252a43;
  margin-bottom: 0;
  padding-top: 10px;
}
.modal-title > .uploaded-date {
  font-size: 16px;
  font-weight: 600;
  color: #aaaaaa;
}
.my-modal-footer {
  display: flex;
  justify-content: center;
  margin-top: 12px;
  margin-bottom: 12px;
}

.my-modal-footer i {
  margin-left: 10px;
  margin-right: 10px;
  font-size: 15px;
  background-color: #eceef0;
  color: #252a43;
  padding: 10px;
  border-radius: 21px;
}
.my-modal-footer i:hover {
  background-color: #252a43;
  color: #eceef0;
  cursor: pointer;
}
.modal-window div:not(:last-of-type) {
  margin-bottom: 8px;
}

.modal-window {
  position: fixed;
  background: rgba(#000000, 0.6);
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 9999999;
  visibility: hidden;
  opacity: 0;
  border-radius: 3px;
  // pointer-events: none;
  transition: all 0.3s;

  // &:target {
  //   visibility: visible;
  //   opacity: 1;
  //   pointer-events: auto;
  // }
  // & > div {
  //   width: 500px;
  //   position: absolute;
  //   top: 50%;
  //   left: 50%;
  //   transform: translate(-50%, -50%);

  //   padding: 25px;
  //   background: #ffffff;
  // }
  .modal-content {
    width: 600px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    padding: 0 25px 25px 25px;
    background: #ffffff;
  }
  header {
    font-weight: bold;
  }
  h1 {
    font-size: 150%;
    margin: 0 0 15px;
  }
}




# in your page component  html add this content


  <div id="open-modal" class="modal-window" [ngStyle]="modal_style">
    <div class="modal-content" style="width:600px;">
      <a title="Close" class="modal-close" (click)="editDialog(false)">
        <i class="far fa-times-circle"></i>
      </a>
      <div class="modal-title">
        <div style="flex-grow: 1;">
          <h1> 'Create Budget Item'</h1>
        </div>
      </div>
      <div class="my-modal-body">
        <div class="row">
          <div class="col-md-12">
            <h1>Hi</h1>
          </div>
        </div>

        <div class="row">
          <div class="col-md-12 text-right">
            <button
              mat-raised-button
              color="primary"
              [disabled]="itemForm.invalid"
              (click)="saveItem()"
            >
              Save
            </button>
            <button mat-raised-button color="primary" (click)="editDialog(false)">
              <mat-icon>close</mat-icon>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>


# In Component ts 


  modelv = false;
  modal_style = {
    visibility: 'hidden',
    opacity: 0
  };
  editDialog(visible: boolean, item: any = null) {
     if (this.modelv != visible) {
      this.modelv = visible;
      if (this.modelv) {
        this.modal_style = {
          visibility: 'visible',
          opacity: 1
        };
      } else {
        this.modal_style = {
          visibility: 'hidden',
          opacity: 0
        };
      }
    }
  }



dialog component using only angular and css 
