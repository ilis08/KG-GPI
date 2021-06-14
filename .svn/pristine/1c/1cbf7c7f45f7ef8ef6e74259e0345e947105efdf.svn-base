using System;
using System.Collections.Generic;
using System.Drawing;
using System.Drawing.Drawing2D;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Draw.src.Model
{
	[Serializable]
    public class NewPrimitive : Shape
    {
		#region Constructor
		public NewPrimitive()
		{

		}
		public NewPrimitive(Shape shape) : base(shape)
		{

		}

		public NewPrimitive(RectangleF rect) : base(rect)
		{
		}

		public NewPrimitive(RectangleShape rectangle) : base(rectangle)
		{
		}

		#endregion

		/// <summary>
		/// Проверка за принадлежност на точка point към правоъгълника.
		/// В случая на правоъгълник този метод може да не бъде пренаписван, защото
		/// Реализацията съвпада с тази на абстрактния клас Shape, който проверява
		/// дали точката е в обхващащия правоъгълник на елемента (а той съвпада с
		/// елемента в този случай).
		/// </summary>
		public override bool Contains(PointF point)
		{
			int a = (int)Width / 2, b = (int)Height / 2;
			Point centreOfEllipse = new Point((int)(Location.X + a), (int)(Location.Y + b));
			int left = (int)(Math.Pow((point.X - centreOfEllipse.X), 2) / Math.Pow(a, 2));
			int right = (int)(Math.Pow((point.Y - centreOfEllipse.Y), 2) / Math.Pow(b, 2));
			if (left + right <= 0)
			{
				return true;
			}
			return false;
		}

		/// <summary>
		/// Частта, визуализираща конкретния примитив.
		/// </summary>
		public override void DrawSelf(Graphics grfx)
		{
			GraphicsPath path = new GraphicsPath();
			path.AddEllipse(new RectangleF(Rectangle.X, Rectangle.Y, Rectangle.Width + 100, Rectangle.Height + 100));


			if (BorderWidth != 0)
			{
				grfx.DrawPath(new Pen(Color.FromArgb(Transparency, BorderColor), BorderWidth), path);
				grfx.DrawLine(Pens.Black, Location.X + (Width - 60), Location.Y + 22 , Location.X + (Width - 60), Location.Y + Height * 1.75f);
				grfx.DrawLine(Pens.Black, Location.X + (Width), Location.Y, Location.X + (Width), Location.Y + Height * 2);
				grfx.DrawLine(Pens.Black, Location.X + (Width + 60), Location.Y + 22, Location.X + (Width + 60), Location.Y + Height * 1.75f);
				grfx.DrawLine(Pens.Black, Location.X + (Width * 2), Location.Y + (Width), Location.X + (Width / 45), Location.Y + (Height));
			}
			grfx.FillPath(new SolidBrush(Color.FromArgb(Transparency, FillColor)), path);
		}
	}
}
