#include<graphics.h>
#include<iostream>
int radii = 2;
int color = 0;
void boundaryfill(int x,int y, int fill, int boundary)
	{
		int current;
		current=getpixel(x,y);
		if((current!=boundary)&&(current!=fill))
		{
			setcolor(fill);
			putpixel(x,y,fill);
			boundaryfill(x+1,y,fill,boundary);
			boundaryfill(x,y-1,fill,boundary);
			boundaryfill(x-1,y,fill,boundary);
			boundaryfill(x,y+1,fill,boundary);
		}
	}
    void camera()
	{
		outtextxy(25,355,(char*)"Save");
		outtextxy(30,370,(char*)"as");
		outtextxy(25,385,(char*)"image");
	}  
	
	void clear()
	{
		outtextxy(25,420,(char*)"clear");
		outtextxy(30,437,(char*)"all");
	}
	
	void eraser()
	{
		outtextxy(25,320,(char*)"Erase");
	}
    void setup()
	{
		setcolor(1);
		//status:
		outtextxy(13,580,(char*)"Status: ");
		setcolor(8);
		//main bordeer
		rectangle(80,0,995,676);
		rectangle(81,1,994,675);
		
		//tool box 
		rectangle(10,170,74,468);
		rectangle(11,171,73,467);
		
		//size outline
		rectangle(10,474,74,560);
		rectangle(11,475,73,559);
		outtextxy(28,540,(char*)"SIZE");
		outtextxy(26,489,(char*)"1");
		outtextxy(52,489,(char*)"2");
		outtextxy(26,516,(char*)"3");
		outtextxy(52,516,(char*)"4");
		
		
		// brush size box
		rectangle(18,484,40,508);
		rectangle(44,484,66,508);
		
		rectangle(18,512,40,536);
		rectangle(44,512,66,536);
		
		
		
		//colors box
		rectangle(18,180,40,200);
		rectangle(44,180,66,200);
		
		rectangle(18,204,40,224);
		rectangle(44,204,66,224);
		
		rectangle(18,228,40,248);
		rectangle(44,228,66,248);
		
		rectangle(18,252,40,272);
		rectangle(44,252,66,272);
		
		rectangle(18,276,40,296);
		rectangle(44,276,66,296);
		
		//eraser box
		eraser();
		rectangle(18,300,66,350);
		
		//save pic
		camera();
		rectangle(18,354,66,404);
		
		// clear all
		clear();
		rectangle(18,408,66,458);
		
		
		
		boundaryfill(12,174,7,8);
		
		boundaryfill(12,476,7,8);
		
		boundaryfill(19,181,0,8);
		boundaryfill(45,181,5,8);
			
		boundaryfill(19,205,1,8);
		boundaryfill(45,205,2,8);
		
		boundaryfill(19,229,4,8);
		boundaryfill(45,229,14,8);
		
		boundaryfill(19,253,3,8);
		boundaryfill(45,253,6,8);
		
		boundaryfill(19,277,12,8);
		boundaryfill(45,277,9,8);
	}
	
void drawingpad()
	{
		POINT cursorpos;
		setup();
		while(1)
		{
			setcolor(color);
			GetCursorPos(&cursorpos);//to get screen co-ordinate
			ScreenToClient(GetForegroundWindow(),&cursorpos);//to convert screen co-ordinate to window co-ordinate
			if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>81&&cursorpos.x<994&&cursorpos.y>1&&cursorpos.y<675)//getkeystate detects the mouse left button press
			{
				circle(cursorpos.x,cursorpos.y,radii);	
				boundaryfill(cursorpos.x,cursorpos.y,color,color);
			}
			
			//Color black
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<40&&cursorpos.y>180&&cursorpos.y<200)
			{
				color=0;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color magenta
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>44&&cursorpos.x<66&&cursorpos.y>180&&cursorpos.y<200)
			{
				color=5;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color blue
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<40&&cursorpos.y>204&&cursorpos.y<224)
			{
				color=1;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color green
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>44&&cursorpos.x<66&&cursorpos.y>204&&cursorpos.y<224)
			{
				color=2;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color red
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<40&&cursorpos.y>228&&cursorpos.y<248)
			{
				color=4;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color yellow
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>44&&cursorpos.x<66&&cursorpos.y>228&&cursorpos.y<248)
			{
				color=14;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color cyan
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<40&&cursorpos.y>252&&cursorpos.y<272)
			{
				color=3;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color Brown
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>44&&cursorpos.x<66&&cursorpos.y>252&&cursorpos.y<272)
			{
				color=6;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color light red
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<40&&cursorpos.y>276&&cursorpos.y<296)
			{
				color=12;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
			//Color light red
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>44&&cursorpos.x<66&&cursorpos.y>276&&cursorpos.y<296)
			{
				color=9;
				setcolor(8);
				outtextxy(13,598,(char*)"Marker     ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			
				//Eraser
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<66&&cursorpos.y>300&&cursorpos.y<350)
			{
				color=15;
				setcolor(8);
				outtextxy(13,598,(char*)"Eraser      ");
				outtextxy(13,615,(char*)"In Use    ");
			}
			//save image
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<66&&cursorpos.y>354&&cursorpos.y<404)
			{
 				
				writeimagefile("image.jpg",82,2,993,674);
				setcolor(8);
				outtextxy(13,598,(char*)"Snapshot");
				outtextxy(13,615,(char*)"Taken ");
				
			}
			//Clear all
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<66&&cursorpos.y>408&&cursorpos.y<458)
			{
				cleardevice();
				setup();
				setcolor(8);
				outtextxy(13,598,(char*)"Cleared    ");
				outtextxy(13,615,(char*)"All      ");
			}
			//Brushsize
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<40&&cursorpos.y>484&&cursorpos.y<508)
			{
				radii=2;
				setcolor(8);
				outtextxy(13,598,(char*)"Brush      ");
				outtextxy(13,615,(char*)"2px      ");
			}
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>44&&cursorpos.x<66&&cursorpos.y>484&&cursorpos.y<508)
			{
				radii=6;
				setcolor(8);
				outtextxy(13,598,(char*)"Brush     ");
				outtextxy(13,615,(char*)"6px      ");
			}
			
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>18&&cursorpos.x<40&&cursorpos.y>512&&cursorpos.y<536)
			{
				radii=10;
				setcolor(8);
				outtextxy(13,598,(char*)"Brush      ");
				outtextxy(13,615,(char*)"10px      ");
			}
			
			else if(((GetKeyState(VK_LBUTTON) & 0x8000) != 0)&&cursorpos.x>44&&cursorpos.x<66&&cursorpos.y>512&&cursorpos.y<536)
			{
				radii=14;
				setcolor(8); 
				outtextxy(13,598,(char*)"Brush      ");
				outtextxy(13,615,(char*)"14px      ");
			}
		}
		
		
	}
    int main()
{
	
	initwindow(1000,680,"simple drawing appilcation");
	setbkcolor(WHITE);
	cleardevice(); 
	cleardevice();
	drawingpad();//main drawing canvas
	getch();
	closegraph();
}
