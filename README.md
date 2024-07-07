توضیح crud.py:

این کد، مجموعه‌ای از توابع CRUD (Create, Read, Update, Delete) را برای مدیریت جداول دانشجو (Student)، استاد (Professor) و درس (Course) در پایگاه داده ارائه می‌دهد. در اینجا توضیح خط به خط این کد آمده است:
from sqlalchemy.orm import Session
import sys
from pathlib import Path
sys.path[0] = str(Path(sys.path[0]).parent)

from project import models , schemas

from sqlalchemy.orm import Session: ماژول Session را از sqlalchemy.orm وارد می‌کند که برای مدیریت نشست‌های پایگاه داده استفاده می‌شود.
from pathlib import Path: این‌ها برای تنظیم مسیر سیستم استفاده می‌شوند تا مطمئن شوند که ماژول‌های پروژه به درستی وارد می‌شوند.
from project import models , schemas: مدل‌ها و اسکیماهای پروژه را وارد می‌کند.

توابع مرتبط با جدول دانشجو student:

تابع get_student:
این تابع یک شناسه دانشجو (student_id) را می‌گیرد و دانشجوی مربوطه را از پایگاه داده واکشی می‌کند.

تابع create_student:
این تابع یک شیء schemas.Student را می‌گیرد و یک رکورد جدید دانشجو را در پایگاه داده ایجاد می‌کند.

تابع removestudent:
این تابع یک شناسه دانشجو (Student_id) را می‌گیرد و دانشجوی مربوطه را از پایگاه داده حذف می‌کند.

تابع update_student:
این تابع یک شناسه دانشجو (student_id) و یک شیء models.Student را می‌گیرد و اطلاعات دانشجوی مربوطه را به‌روزرسانی می‌کند.

توابع مرتبط با استاد professor:

تابع get_professor:
این تابع یک شناسه استاد (Professor_id) را می‌گیرد و استاد مربوطه را از پایگاه داده واکشی می‌کند.

تابع create_professor:
این تابع یک شیء schemas.Professor را می‌گیرد و یک رکورد جدید استاد را در پایگاه داده ایجاد می‌کند.

تابع update_professor:
این تابع یک شیء schemas.Professor را می‌گیرد و یک رکورد جدید استاد را در پایگاه داده ایجاد می‌کند.

تابع removeprofessor:
این تابع یک شناسه استاد (Professor_id) را می‌گیرد و استاد مربوطه را از پایگاه داده حذف می‌کند

توابع مرتبط با جدول درس course:

تابع get_course:
این تابع یک شناسه درس (Course_id) را می‌گیرد و درس مربوطه را از پایگاه داده واکشی می‌کند.

تابع create_course:
این تابع یک شیء schemas.Course را می‌گیرد و یک رکورد جدید درس را در پایگاه داده ایجاد می‌کند.

تابع update_course:
این تابع یک شناسه درس (course_id) و یک شیء models.Course را می‌گیرد و اطلاعات درس مربوطه را به‌روزرسانی می‌کند.

تابع removecourse:
این تابع یک شناسه درس (Course_id) را می‌گیرد و درس مربوطه را از پایگاه داده حذف می‌کند.