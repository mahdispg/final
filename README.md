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
def get_student(db: Session, student_id: int):
    return db.query(models.Student).filter(models.Student.stid == student_id).first()
این تابع یک شناسه دانشجو (student_id) را می‌گیرد و دانشجوی مربوطه را از پایگاه داده واکشی می‌کند.

تابع create_student:
def create_student(db: Session, student: schemas.Student):
    db_student = models.Student(
        stid=student.stid ,
        fname=student.fname,
        lname=student.lname,
        father=student.father,
        birth=student.birth,
        ids=student.ids,
        borncity=student.borncity,
        address=student.address,
        postalcode=student.postalcode,
        cphone=student.cphone,
        hphone=student.hphone,
        department=student.department,
        major=student.major,
        married=student.married,
        id=student.id,
        scourseids=student.scourseids,
        lids=student.lids,
    )
    db.add(db_student)
    db.commit()
    db.refresh(db_student)
    return db_student
این تابع یک شیء schemas.Student را می‌گیرد و یک رکورد جدید دانشجو را در پایگاه داده ایجاد می‌کند.

تابع removestudent:
def removestudent(db: Session , Student_id: int):
    db_student = db.query(models.Student).filter(models.Student.stid == Student_id).first()
    db.delete(db_student)
    db.commit()
این تابع یک شناسه دانشجو (Student_id) را می‌گیرد و دانشجوی مربوطه را از پایگاه داده حذف می‌کند.

تابع update_student:
def update_student(db: Session, student_id: str, student: models.Student):
    db_student = db.query(models.Student).filter(models.Student.stid == student_id).first()
    if db_student is None:
        return db_student
    else:
        for key, value in student.dict().items():
            setattr(db_student, key, value)
        db.commit()
        db.refresh(db_student)
        return db_student
این تابع یک شناسه دانشجو (student_id) و یک شیء models.Student را می‌گیرد و اطلاعات دانشجوی مربوطه را به‌روزرسانی می‌کند.