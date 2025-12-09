/* Portrait mode: deliberately overlapped */
@media screen and (orientation: portrait) {
  h1 {
    position: absolute;
    top: 50px;
    left: 30px;
    z-index: 2; /* sits above text */
  }
  .static-text {
    position: absolute;
    top: 60px;   /* overlaps with heading */
    left: 20px;
    width: 90%;
    background: rgba(0,0,0,0.4);
    z-index: 1;
  }
  .button-area {
    position: absolute;
    top: 80px;   /* overlaps both heading and text */
    left: 40px;
    z-index: 3;
  }
}
