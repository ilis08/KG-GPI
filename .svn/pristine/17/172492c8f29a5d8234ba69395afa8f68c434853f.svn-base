using System;
using System.Drawing;
using System.Collections.Generic;
using System.Windows.Forms;
using System.Drawing.Drawing2D;

namespace Draw
{
	/// <summary>
	/// Класът, който ще бъде използван при управляване на дисплейната система.
	/// </summary>
	public class DisplayProcessor
	{
		#region Constructor

		public DisplayProcessor()
		{
		}

		#endregion

		#region Properties

		/// <summary>
		/// Списък с всички елементи формиращи изображението.
		/// </summary>
		/// 
		/// 
		#endregion

		#region Drawing

		/// <summary>
		/// Прерисува всички елементи в shapeList върху e.Graphics
		/// </summary>
		public void ReDraw(object sender, PaintEventArgs e, DoubleBufferedPanel panel)
		{
			e.Graphics.SmoothingMode = SmoothingMode.AntiAlias;
			Draw(e.Graphics, panel);
		}

		/// <summary>
		/// Визуализация.
		/// Обхождане на всички елементи в списъка и извикване на визуализиращия им метод.
		/// </summary>
		/// <param name="grfx">Къде да се извърши визуализацията.</param>
		public virtual void Draw(Graphics grfx, DoubleBufferedPanel panel)
		{
			foreach (Shape item in panel.ShapeList)
			{
				DrawShape(grfx, item);
			}
		}

		/// <summary>
		/// Визуализира даден елемент от изображението.
		/// </summary>
		/// <param name="grfx">Къде да се извърши визуализацията.</param>
		/// <param name="item">Елемент за визуализиране.</param>
		public virtual void DrawShape(Graphics grfx, Shape item)
		{
            if (item.Rotation != 0)
            {
				Matrix matrix = new Matrix();
				matrix.RotateAt(item.Rotation, new PointF(item.Location.X + item.Width / 2, item.Location.Y + item.Height / 2));
				grfx.MultiplyTransform(matrix);
				item.DrawSelf(grfx);
				grfx.ResetTransform();
			}
            else
            {
				item.DrawSelf(grfx);
            }
		}

		#endregion
	}
}
