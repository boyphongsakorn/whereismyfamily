<script>
  //import svelteLogo from './assets/svelte.svg'
  //import Counter from './lib/Counter.svelte'
  let findwho,findwhoth,whatyouwant,phonenumber;
  import { Styles,Container,FormGroup,Label,Input,Form } from 'sveltestrap';

  function who(player){
    if(player == 'boy'){
      whatyouwant = 'express'
    }else if(player == 'cht'){
      phonenumber = '0624892914'
    }else{
      whatyouwant = ''
    }
    findwho = player;
    return true;
  }
  function myNewFunction(sel) {
    //alert(sel.options[sel.selectedIndex].text);
    findwhoth = sel.options[sel.selectedIndex].text;
  }
</script>

<Styles />

  <Container sm>
    <h3 class="bg-light">ไม่เจอใครอยู่บ้านหรอ?</h3>
        <Label for="exampleSelect">คุณต้องการติดต่อใคร?</Label>
        <Input type="select" value="def" on:change={(e)=>{who(e.target.value);myNewFunction(e.target);}}>
          <option value="def">เลือกคุณที่ต้องการติดต่อ</option>
          <option value="boy">พงศกร</option>
          <option value="cht">ชัชวาลย์</option>
          <option value="dawn">ดวงจันทร์</option>
          <option value="pukbung">พัชรธิดา</option>
          <option value="someone">ใครก็ได้ที่ใกล้ที่สุด</option>
          <option value="who">ไม่มีชื่ออยู่ในนี้</option>
        </Input>
    {#if findwho == 'boy'}
      <br>
      <Label for="exampleSelect">ต้องการติดต่อพงศกร เรื่องอะไร?</Label>
      <Input type="select" value="express" on:change={(e)=>whatyouwant=e.target.value}>
        <option value="express">ส่งของ/ส่งจดหมาย</option>
        <option value="boy">เซ็นจดหมาย</option>
        <option value="cht">ติดต่อให้ทำงาน/ซ่อมคอม/ซ่อมมือถือ</option>
      </Input>
    {/if}
    {#if findwho == 'cht'}
      <br>
      <Label for="exampleSelect">ต้องการติดต่อชัชวาลย์ เรื่องอะไร?</Label>
      <Input type="select" value="express" on:change={(e)=>whatyouwant=e.target.value}>
        <option value="contact">ติดต่อ</option>
        <option value="other">อื่นๆ</option>
      </Input>
    {/if}
    {#if whatyouwant == 'express'}
      ถ้าเป็นของหรือจดหมายที่ต้องจ่ายเงิน กดปุ่มโทร หรือ เบอร์โทร 080-164-3864
      <a href="tel:0801643864" class="btn btn-primary">โทร</a>
    {/if}
    {#if whatyouwant == 'contact'}
      ต้องการติดต่อ {findwhoth} กดปุ่มโทร หรือ เบอร์โทร {phonenumber}
      <a href="tel:{phonenumber}" class="btn btn-primary">โทร</a>
    {/if}
  </Container>

<style>
  /*.logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }*/
</style>
