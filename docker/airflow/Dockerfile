FROM apache/airflow:2.9.2


ENV PYTHONPATH="/opt/airflow/dags"

# Install poetry
RUN pip install poetry
ENV PATH="${PATH}:/root/.local/bin"


# Copy project files
COPY dags /opt/airflow/dags
COPY scripts /opt/airflow/scripts
COPY data /opt/airflow/data
COPY pyproject.toml poetry.lock /opt/airflow/
COPY visualization /opt/airflow/visualization
COPY README.md /opt/airflow/README.md


# Install dependencies using Poetry
RUN poetry install --no-interaction

# set up working directory
WORKDIR /opt/airflow

# change owner of the directory to airflow user
RUN chown -R airflow /opt/airflow/scripts

# switch back to airflow user
USER airflow

