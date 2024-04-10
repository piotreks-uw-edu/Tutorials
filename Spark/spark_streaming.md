### filer a DataFrame from now
import java.time.LocalDateTime
import java.time.temporal.ChronoUnit

val now = LocalDateTime.now()
val filtered_df = dfProcessed.filter($"timestamp" > now)

