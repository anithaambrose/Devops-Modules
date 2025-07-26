#----STAGE-1:BUILDER-------
FROM python:3.10-slim AS builder
WORKDIR /app
#install build dependencies
RUN apt-get update && apt-get install -y build-essential
#copy requirements , Code & install dependencies
COPY requirements.txt  .
COPY app.py .
RUN pip install --prefix=/install -r requirements.txt

#----STAGE-2:FINAL IMAGE------
FROM python:3.10-slim 
WORKDIR /app
#Copy dependencies & app from builder stage
COPY --from=builder /app/app.py .
COPY --from=builder /install /usr/local
#Expose app port
EXPOSE 5001
#start the fask app
CMD ["python","app.py"]
 
