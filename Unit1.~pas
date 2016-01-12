unit Unit1;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ClipBrd, ExtCtrls;

type
  TForm1 = class(TForm)
    Button1: TButton;
    Button2: TButton;
    Button3: TButton;
    Button4: TButton;
    ListBox1: TListBox;
    Button5: TButton;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure Button3Click(Sender: TObject);
    procedure Button4Click(Sender: TObject);
    procedure Button5Click(Sender: TObject);


  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.dfm}

procedure TForm1.Button1Click(Sender: TObject);
begin
    if findwindow(nil,'Корзина')<>0
      then begin
           showmessage('окно имеется в наличии');
           setwindowpos(findwindow(nil,'Корзина'),HWND_BOTTOM,1,1,1000,1000,HWND_TOP);
           end
      else showmessage('окно отсутствует');

end;

procedure TForm1.Button2Click(Sender: TObject);
begin
  if findwindow(nil,'Корзина')<>0
    then
      begin
      setwindowtext(findwindow(nil,'Корзина'),'мусорная корзина');
      if isIconic(findwindow(nil,'мусорная корзина'))
        then OpenIcon(findwindow(nil,'мусорная корзина'))
        else CloseWindow(findwindow(nil,'мусорная корзина'));
      end
      else       showmessage('okno otsutstvuet');
end;

procedure TForm1.Button3Click(Sender: TObject);
begin
    if findwindow(nil,'мусорная корзина')<>0
      then
        begin
        setwindowtext(findwindow(nil,'мусорная корзина'),'Корзина');
        if isIconic(findwindow(nil,'Корзина'))
          then OpenIcon(findwindow(nil,'Корзина'))
          else CloseWindow(findwindow(nil,'Корзина'));
        end
        else       showmessage('окно отсутствует');
end;

function EnumProc (Wd: Hwnd; Param: Longint): Boolean;stdcall;
Var
 Nm:Array[0..255] of Char;
 Cs: Array[0..255] of Char;
 begin
 getwindowtext(Wd,Nm,255);
 getclassname(Wd,Cs,255);
 if Wd <> Form1.Handle then
 Form1.ListBox1.Items.Add(string(Nm)+'/'+String(cs));
 EnumProc := TRUE;
 end;


procedure TForm1.Button4Click(Sender: TObject);
begin
  ListBox1.Items.Clear;
  EnumWindows (@EnumProc,0);
end;
 procedure TForm1.Button5Click(Sender: TObject);
 var hnd:thandle;
 canvas:tcanvas;
 dc:hdc;
 x,y:real;
 m,n:longint;
 a,b:integer;
 WinDc:HDC;
 Arect:Trect;
 result:Tbitmap;
 begin
  hnd:=findwindow(nil,'Корзина');
  result:=tbitmap.create;
  GetWindowRect(hnd,Arect);
  with result, arect do
    begin
      a :=Arect.Right-Arect.Left;
      b := Arect.Bottom-Arect.Top;
    end;
  canvas:=tcanvas.Create;
  dc:=getdc(hnd);
  showmessage(inttostr(dc));
  with canvas do
   begin
    handle:=dc;
    rectangle(0,0,a,b);
    for  m:= 0 to a do
      begin
        x:= m*4*Pi/a;
        y:=sin(x);
        n:=trunc(b-(y+1)*b/2);
        Canvas.LineTo(m,n);
      end;
   free;
   end;
result.Free;
end;

end.



